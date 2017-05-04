---
title: "逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件 | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件
  SharePoint 2010 使用 OData 公開其清單資料。  在 SharePoint 中， OData 服務是由 RESTful 服務 ListData.svc 實作。  本篇將逐步解說並示範如何建立裝載 Silverlight 應用程式的 SharePoint Web 組件。  藉由使用 ListData.svc，Silverlight 應用程式可以顯示 SharePoint 公告清單資訊。  如需詳細資訊，請參閱 [SharePoint Foundation REST 介面](http://go.microsoft.com/fwlink/?LinkId=225999) 和 [開啟資料通訊協定](http://go.microsoft.com/fwlink/?LinkId=226000)。  
  
 本逐步解說將示範下列工作：  
  
-   [建立 Silverlight 應用程式與 Silverlight Web 組件](#BKMK_creatingSLApp)。  
  
-   [自訂 Silverlight 應用程式](#BKMK_customizeSLApp)。  
  
-   [自訂 Silverlight 應用程式](#BKMK_customizeSLApp)。  
  
-   [自訂 Silverlight 應用程式](#BKMK_customizeSLApp)。  
  
-   [測試 Silverlight Web 組件](#BKMK_testSLApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> 建立 Silverlight 應用程式與 Silverlight Web 組件  
 首先，在 Visual Studio 中建立 Silverlight 應用程式。  藉由使用 ListData.svc 服務， Silverlight 應用程式從 SharePoint 公告擷取資料清單。  
  
> [!NOTE]  
>  在 4.0 以前 Silverlight 沒有版本支援參考 SharePoint 清單資料所需要的介面。  
  
#### 若要建立 Silverlight 應用程式與 Silverlight Web 組件  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  在範本窗格中，選取 \[**SharePoint 2010 Silverlight Web 組件**\] 範本。  
  
4.  在 \[**名稱**\] 文字方塊中，輸入 SLWebPartTest，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 對話方塊隨即出現。  
  
5.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，輸入您想要偵錯網站定義之 SharePoint 伺服器網站的 URL，或使用預設位置 \(http:\/\/*system name*\/\)。  
  
6.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，選擇 \[**部署為陣列方案**\] 選項按鈕。  
  
     雖然這個範例使用陣列方案，但是 Silverlight Web 組件專案可以部署為陣列或沙箱化方案。  如需沙箱化方案與陣列方案的詳細資訊，請參閱 [沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在 \[**指定 Silverlight 設定資訊**\] 頁面的 \[**要如何關聯 Silverlight Web 組件**\] 區段中，選擇 \[**建立新的 Silverlight 專案並將其與 Web 組件關聯**\] 選項按鈕。  
  
8.  將 \[**名稱**\] 變更為 SLApplication，將 \[**語言**\] 設定為 \[**Visual Basic**\] 或 \[**Visual C\#**\]，然後將 \[**Silverlight 版本**\] 設定為 \[**Silverlight 4.0**\]。  
  
9. 選擇 \[**完成**\] 按鈕。  專案隨即出現在 \[**方案總管**\] 中。  
  
     方案包含兩個專案：Silverlight 應用程式與 Silverlight Web 組件。  Silverlight 應用程式擷取並顯示來自 SharePoint 的清單資料，而 Silverlight Web 組件裝載 Silverlight 應用程式，可讓您在 SharePoint 中檢視它。  
  
##  <a name="BKMK_customizeSLApp"></a> 自訂 Silverlight 應用程式  
 將程式碼和設計項目加入至 Silverlight 應用程式。  
  
#### 若要自訂 Silverlight 應用程式  
  
1.  在 Silverlight 應用程式中加入組件參考至 System.Windows.Data。  如需詳細資訊，請參閱[如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
2.  在 \[**方案總管**\] 中，開啟 \[**參考**\] 的捷徑功能表，然後選擇 \[**加入服務參考**\]。  
  
    > [!NOTE]  
    >  如果您是使用 Visual Basic，則必須選取出現在 \[**方案總管**\] 上方的 \[**顯示所有檔案**\] 圖示，以顯示 \[**參考**\] 節點。  
  
3.  在 \[**加入服務參考**\] 對話方塊的位址方塊中，輸入您的 SharePoint 網站 URL，例如 **http:\/\/MySPSite**，然後選擇 \[**移至**\] 按鈕。  
  
     在 Silverlight 定址 SharePoint OData 服務 ListData.svc 時，它將位址替代為完整服務 URL。  在這個範例中， http:\/\/myserver 成為 http:\/\/myserver\/\_vti\_bin\/ListData.svc。  
  
4.  選擇 \[**確定**\] 按鈕將服務參考加入至專案，並使用預設服務名稱， ServiceReference1。  
  
5.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
6.  加入新的資料來源至以 SharePoint 服務為基礎的專案。  若要這麼做，請在功能表列上選擇 \[**檢視**\]、\[**其他視窗**\]、\[**資料來源**\]。  
  
     \[**資料來源**\] 視窗會顯示所有可用的 SharePoint 清單資料，例如工作、公告和行事曆。  
  
7.  將公告清單資料加入至 Silverlight 應用程式。  您可以將「公告」從 \[**資料來源**\] 視窗拖曳至 Silverlight 設計工具。  
  
     這會建立方格控制項繫結至 SharePoint 網站的公告清單。  
  
8.  調整方格控制項以相容 Silverlight 頁面。  
  
9. 在 MainPage.xaml 程式碼檔 \(Visual C\# 為 MainPage.xaml.cs，Visual Basic 為 MainPage.xaml.vb\)，加入下列命名空間參考。  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. 將下列變數宣告加入至類別的頂端。  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. 以下列程式碼取代 `UserControl_Loaded` 程序。  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     請務必以正在執行 SharePoint 伺服器的名稱取代 *ServerName* 預留位置。  
  
12. 加入下列錯誤處理程序。  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## 修改 Silverlight Web 組件  
 變更 Silverlight Web 組件專案中的屬性，以啟用 Silverlight 偵錯。  
  
#### 若要修改 Silverlight Web 組件  
  
1.  開啟 Silverlight Web 組件專案 \(**SLWebPartTest**\) 的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**屬性**\] 視窗中，選擇 \[**SharePoint**\] 索引標籤。  
  
3.  如果尚未選取，請選取 \[**啟用 Silverlight 偵錯\(而非偵錯的指令碼\)**\] 核取方塊。  
  
4.  儲存專案。  
  
##  <a name="BKMK_testSLApp"></a> 測試 Silverlight Web 組件  
 在 SharePoint 中測試新的 Silverlight Web 組件以確保正確顯示 SharePoint 清單資料。  
  
#### 若要測試 Silverlight Web 組件  
  
1.  按 F5 鍵以建置和執行 SharePoint 方案。  
  
2.  在 SharePoint 的 \[**設置動作**\] 功能表上，選擇 \[**新網頁**\]。  
  
3.  在 \[**新網頁**\] 對話方塊中，輸入標題，例如 SL Web 組件測試，然後選擇 \[**建立**\] 按鈕。  
  
4.  在網頁設計工具，請在 \[**編譯工具**\] 索引標籤上，選取 \[**插入**\]。  
  
5.  在索引標籤區域中，選取 \[**Web 組件**\]。  
  
6.  在 \[**分類**\] 方塊中，選取 \[**自訂**\] 資料夾。  
  
7.  在 \[**Web 組件**\] 清單中，選取 Silverlight Web 組件，然後選擇 \[**加入**\] 按鈕將網頁組件加入至設計工具。  
  
8.  在您進行任何想要進行的動作至 Web 頁面後，請選取 \[**頁面**\] 索引標籤，然後選取工具列的 \[**儲存 & 關閉**\] 按鈕。  
  
     Silverlight Web 組件現在應該會顯示 SharePoint 網站上的資料。  根據預設，頁面儲存在 SharePoint 的網站頁面清單中。  
  
    > [!NOTE]  
    >  當在 Silverlight 跨網域存取資料時， Silverlight 會防範可能利用 Web 應用程式的安全性弱點。  如果您在 Silverlight 存取遠端資料時遇到問題，請參閱 [讓服務可在存取跨定義域界限時使用](http://go.microsoft.com/fwlink/?LinkId=223276)。  
  
## 請參閱  
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  