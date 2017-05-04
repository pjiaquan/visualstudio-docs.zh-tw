---
title: "逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IntelliTrace [Visual Studio 中的 SharePoint 開發]"
  - "獨立資料收集器"
  - "Visual Studio 中的 SharePoint 程式開發，IntelliTrace"
  - "資料收集器"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式
  透過使用 IntelliTrace，您可以更輕鬆地偵錯 SharePoint 方案。  傳統的偵錯工具只會顯示目前時間的方案快照。  但是，您可以使用 IntelliTrace 來檢閱方案內發生的過去事件以及事件發生所在的內容，也可以用於巡覽程式碼。  
  
 以下將示範如何使用 Microsoft 監視代理程式偵錯 Visual Studio Ultimate 的 SharePoint 2010 或 SharePoint 2013 專案，並從部署的應用程式收集 IntelliTrace 資料。  為分析資料，您必須使用 Visual Studio Ultimate。  此專案會併入功能接收器，當啟用此功能時，它會將工作加入至工作清單，並將公告加入至公告清單。  當停用此功能時，此工作會標示為已完成，並將第二個公告加入至公告清單。  但是，此程序包含一個邏輯錯誤，該錯誤使得專案無法正確執行。  您可以藉由使用 IntelliTrace 來尋找並更正此錯誤。  
  
 **適用於:** 本主題資訊適用於在 Visual Studio 中建立的 SharePoint 2010 或 SharePoint 2013 方案。  
  
 這個逐步解說將說明下列工作：  
  
-   [建立功能接收器](#BKMK_CreateReceiver)  
  
-   [將程式碼加入至功能接收器](#BKMK_AddCode)  
  
-   [測試專案](#BKMK_Test1)  
  
-   [使用 Microsoft 監視代理程式收集 IntelliTrace 的資料。](#BKMK_CollectDiagnosticData)  
  
-   [偵錯和修正 SharePoint 方案](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 和 SharePoint 版本。  請參閱 [開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio Ultimate  
  
##  <a name="BKMK_CreateReceiver"></a> 建立功能接收器  
 首先，您要建立具有功能接收器的空白 SharePoint 專案。  
  
#### 若要建立功能接收器  
  
1.  建立 SharePoint 2010 或 SharePoint 2013 方案專案，並命名為 IntelliTraceTest。  
  
     隨即出現 \[**SharePoint 自訂精靈**\]，您可以在其中指定專案的 SharePoint 網站及方案的信任層級。  
  
2.  選取 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**結束**\] 按鈕。  
  
     IntelliTrace 只會在陣列方案上操作。  
  
3.  在 \[**方案總管**\] 中，開啟 \[**功能**\] 節點的捷徑功能表，然後選擇 \[**加入功能**\]。  
  
     隨即出現 Feature1.feature。  
  
4.  開啟 Feature1.feature 的捷徑功能表，然後選擇 \[**加入事件接收器**\] ，將程式碼模組加入至功能。  
  
##  <a name="BKMK_AddCode"></a> 將程式碼加入至功能接收器  
 接下來，將程式碼加入至功能接收器中的兩個方法：`FeatureActivated` 和 `FeatureDeactivating`。  每當分別在 SharePoint 中啟用或停用功能時，都會觸發這些方法。  
  
#### 若要將程式碼加入至功能接收器  
  
1.  在 `Feature1EventReceiver` 類別頂端，加入下列程式碼宣告可指定 SharePoint 網站與子網站的變數：  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  以下列程式碼取代 `FeatureActivated` 方法：  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  以下列程式碼取代 `FeatureDeactivating` 方法：  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> 測試專案  
 既然已加入程式碼至功能接收器，而且資料收集器正在執行，請部署並執行 SharePoint 方案以測試它是否正確運作。  
  
> [!IMPORTANT]  
>  對於此範例，錯誤會在 FeatureDeactivating 事件處理常式中拋出。  在之後的解說之中，您將利用資料收集器建立的 .iTrace 檔案找出錯誤所在位置。  
  
#### 若要測試專案  
  
1.  將方案部署至 SharePoint，然後在瀏覽器中開啟 SharePoint 網站。  
  
     此功能會自動啟用，使得它的功能接收器加入公告和工作。  
  
2.  顯示公告和工作清單的內容。  
  
     在公告清單中應有名為 **Activated feature: IntelliTraceTest\_Feature1** 的新公告，以及已加入至工作清單的 **Deactivate feature: IntelliTraceTest\_Feature1** 新工作。  如果這些項目的發生部份遺失，請確認功能是否已啟動。  如果未啟動，請啟動它。  
  
3.  執行下列步驟以停用功能：  
  
    1.  在 SharePoint 中的 \[**選單**\] 索引標籤上，選擇 \[**網站設定**\]。  
  
    2.  在 \[**設置動作**\] 下，選擇 \[**管理網站的功能。**\] 連結。  
  
    3.  在 \[**IntelliTraceTest Feature1**\] 旁邊，請選擇 \[**停止**\] 按鈕。  
  
    4.  在警告頁面上，選擇 \[**停用這個功能。**\] 連結。  
  
     FeatureDeactivating\(\) 事件處理常式拋出錯誤。  
  
##  <a name="BKMK_CollectDiagnosticData"></a> 使用 Microsoft 監視代理程式收集 IntelliTrace 的資料。  
 當您將 Microsoft 監視代理程式安裝在執行 SharePoint 的系統上時，您可以使用比 IntelliTrace 回傳資訊更加特定的資料，以對 SharePoint 方案進行偵錯。  當執行 SharePoint 方案時，代理程式使用 PowerShell cmdle 擷取偵錯資訊以在 Visual Studio 外部進行作業。  
  
> [!NOTE]  
>  本章節中的組態資訊將針對此範例作說明。  如需其他組態選項的詳細資訊，請參閱 [使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
1.  在執行 SharePoint 的電腦上， [設定 Microsoft 監視代理程式並開始監視您的方案](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
2.  停用功能：  
  
    1.  在 SharePoint 中的 \[**選單**\] 索引標籤上，選擇 \[**網站設定**\]。  
  
    2.  在 \[**設置動作**\] 下，選擇 \[**管理網站的功能。**\] 連結。  
  
    3.  在 \[**IntelliTraceTest Feature1**\] 旁邊，請選擇 \[**停止**\] 按鈕。  
  
    4.  在警告頁面上，選擇 \[**停用這個功能。**\] 連結。  
  
     錯誤發生 \(在此例中，主因為在 FeatureDeactivating\(\) 事件處理常式中所拋出的錯誤\)。  
  
3.  在 PowerShell 命令視窗，請 [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) 執行命令以建立 .iTrace 檔案，停止監視，並重新啟動您的 SharePoint 方案。  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> 偵錯和修正 SharePoint 方案  
 現在您可以在 Visual Studio 中，檢視 IntelliTrace 紀錄檔，以尋找並修正在 SharePoint 方案的錯誤。  
  
#### 若要偵錯和修正 SharePoint 方案  
  
1.  在 \\IntelliTraceLogs \\資料夾，請開啟 Visual Studio 中的 .iTrace 檔案。  
  
     \[**IntelliTrace 摘要**\] 頁面隨即出現。  由於錯誤未被處理， SharePoint 相互關聯 ID \(GUID\) 出現在 \[**分析**\] 區段中的未處理例外狀況區域。  如果您要檢視發生錯誤的呼叫堆疊，選擇 \[**呼叫堆疊**\] 按鈕。  
  
2.  選擇 \[**偵錯例外狀況。**\] 按鈕。  
  
     如果有提示，請載入符號檔。  在 \[**IntelliTrace**\] 視窗中，例外狀況將會反白顯示，如「擲回：發生嚴重錯誤\!」。  
  
     在 IntelliTrace 視窗中，選擇例外狀況以顯示發生錯誤的程式碼。  
  
3.  開啟 SharePoint 方案後 ，註解或移除在 FeatureDeactivating\(\) 程式頂端的 **throw**陳述式，以修正錯誤。  
  
4.  重建 Visual Studio 中的方案，並重新部署至 SharePoint。  
  
5.  執行下列步驟以停用功能：  
  
    1.  在 SharePoint 中的 \[**選單**\] 索引標籤上，選擇 \[**網站設定**\]。  
  
    2.  在 \[**設置動作**\] 下，選擇 \[**管理網站的功能。**\] 連結。  
  
    3.  在 \[**IntelliTraceTest Feature1**\] 旁邊，請選擇 \[**停止**\] 按鈕。  
  
    4.  在警告頁面上，選擇 \[**停用這個功能。**\] 連結。  
  
6.  開啟工作清單，並確認 Deactivate 工作的 \[**狀態**\] 值為「已完成」，而且其 \[**% 完成**\] 值為 100%。  
  
     現在程式碼正適當地執行。  
  
## 請參閱  
 [驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [使用 IntelliTrace](../debugger/intellitrace.md)   
 [逐步解說：使用單元測試驗證 SharePoint 程式碼](http://msdn.microsoft.com/zh-tw/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  