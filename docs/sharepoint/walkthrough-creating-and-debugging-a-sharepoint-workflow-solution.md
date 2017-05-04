---
title: "逐步解說：建立並偵錯 SharePoint 工作流程方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 工作流程"
  - "工作流程 [Visual Studio 中的 SharePoint 開發]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 逐步解說：建立並偵錯 SharePoint 工作流程方案
  本逐步解說將示範如何建立基本的循序工作流程範本。  工作流程會檢查共用文件庫的屬性，以判斷文件是否已經過檢視。  如果文件已經過檢視，則工作流程會結束。  
  
 這個逐步解說將說明下列工作：  
  
-   在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立 SharePoint 清單定義循序工作流程專案。  
  
-   建立工作流程活動。  
  
-   處理工作流程活動事件。  
  
> [!NOTE]  
>  雖然本逐步解說使用循序工作流程專案，但狀態機器工作流程的程序完全相同。  
>   
>  此外，在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 將屬性加入至 SharePoint 共用文件庫  
 為在 \[**共用文件**\] 庫中追蹤文件的檢視狀態，我們將在 SharePoint 網站上為共用文件建立三個新屬性：`Status`、`Assignee` 和 `Review Comments`。  我們會在 \[**共用文件**\] 庫中定義這些屬性。  
  
#### 若要將屬性加入至 SharePoint 共用文件庫  
  
1.  在 Web 瀏覽器中開啟 SharePoint 網站，例如 http:\/\/\<系統名稱\>\/SitePages\/Home.aspx。  
  
2.  按一下快速啟動列上的 \[**共用文件**\]。  
  
3.  按一下 \[**程式庫工具**\] 功能區上的 \[**程式庫**\]，然後按一下功能區上的 \[**建立欄**\] 按鈕，建立新的資料行。  
  
4.  將該資料行命名為 \[Document Status\]，將它的類型設定為 \[**選項 \(要從中選擇的功能表\)**\]，並指定下列三個選項，然後按一下 \[**確定**\] 按鈕：  
  
    -   **需要檢視**  
  
    -   **檢視完成**  
  
    -   **要求變更**  
  
5.  另外再建立兩個資料行，並分別命名為 \[Assignee\] 和 \[Review Comments\]。  將 \[Assignee\] 資料行類型設定為單行文字，並將 \[Review Comments\] 資料行類型設定為多行文字。  
  
## 啟用不需簽出文件即可進行編輯  
 如果能夠編輯文件而不需將其簽出，則可更容易測試工作流程範本。  在下一個程序中，您將設定 SharePoint 網站來啟用該功能。  
  
#### 啟用不需簽出文件即可進行編輯  
  
1.  按一下快速啟動列上的 \[**共用文件**\] 連結。  
  
2.  按一下 \[**程式庫工具**\] 功能區上的 \[**程式庫**\] 索引標籤，然後按一下 \[**程式庫設定**\] 按鈕，顯示 \[**文件庫設定**\] 頁面。  
  
3.  按一下 \[**一般設定**\] 區段中的 \[**版本設定**\] 連結，顯示 \[**版本控制設定**\] 頁面。  
  
4.  確認 \[**需要先簽出文件才能進行編輯**\] 的設定為 \[**否**\]。  如果不是，請將其變更為 \[**否**\]，然後按一下 \[**確定**\] 按鈕。  
  
5.  關閉瀏覽器。  
  
## 建立 SharePoint 循序工作流程專案  
 循序工作流程是依順序執行直到最後一個活動完成為止的一組步驟。  在此程序中，我們會建立將套用至共用文件清單的循序工作流程。  工作流程精靈會讓您將工作流程與網站定義或清單定義相關聯，以及讓您決定工作流程將在何時啟動。  
  
#### 建立 SharePoint 循序工作流程專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  
  
3.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
4.  在 \[**範本**\] 窗格中，選取 \[**SharePoint 2010 專案**\] 範本。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 MySharePointWorkflow，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
6.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕，以接受信任層級和預設網頁。  
  
     此步驟會將方案的信任層級設定為陣列方案，這是工作流程專案唯一可用的選項。  如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在 \[**方案總管**\] 中，選擇專案節點，然後在功能表列上選擇 \[**專案**\]、\[**加入新項目**\]。  
  
8.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
9. 在 \[**範本**\] 窗格中，選取 \[**循序工作流程 \(僅限陣列方案\)**\] 範本，然後選擇 \[**加入**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
10. 在 \[**指定工作流程名稱進行偵錯**\] 頁面中，接受預設名稱 \(**MySharePointWorkflow \- Workflow1**\)。  保留預設的工作流程範本類型值 \[**清單工作流程**\]，然後按 \[**下一步**\] 按鈕。  
  
11. 在 \[**您要 Visual Studio 在偵錯工作階段中自動關聯工作流程嗎?**\] 頁面中，按 \[**下一步**\] 按鈕接受所有預設設定。  
  
     此步驟會自動將工作流程與共用文件庫相關聯。  
  
12. 在 \[**指定工作流程的啟動條件**\] 頁面上，保留 \[**您要如何啟動工作流程?**\] 區段中選取的預設選項，然後按一下 \[**完成**\] 按鈕。  
  
     此頁面可讓您指定工作流程應於何時開始。  根據預設，當使用者以手動方式在 SharePoint 中啟動工作流程，或當建立工作流程關聯的項目時，就會啟動工作流程。  
  
## 建立工作流程活動  
 工作流程包含一個或多個代表要執行之動作的「*活動*」\(Activity\)。  使用工作流程設計工具可排列工作流程的活動。  在這個程序中，我們會將兩個活動加入至工作流程：HandleExternalEventActivity 和 OnWorkFlowItemChanged。  這些活動會監視 \[**共用文件**\] 清單中的文件檢視狀態。  
  
#### 若要建立工作流程活動  
  
1.  工作流程應會顯示在工作流程設計工具中。  如果沒有，請開啟 \[**方案總管**\] 中的 \[**Workflow1.cs**\] 或 \[**Workflow1.vb**\]。  
  
2.  在設計工具中，選擇 \[**OnWorkflowActivated1**\] 活動。  
  
3.  在 \[**屬性**\] 視窗的 \[**Invoked**\] 屬性旁輸入 onWorkflowActivated，然後按下 ENTER 鍵。  
  
     程式碼編輯器隨即開啟，而且名為 onWorkflowActivated 的事件處理常式方法會加入至 Workflow1 程式檔中。  
  
4.  切換回工作流程設計工具，開啟工具箱，然後展開 \[**Windows Workflow v3.0**\] 節點。  
  
5.  在 \[**工具箱**\] 的 \[**Windows Workflow v3.0**\] 節點，請執行下列其中一組步驟：  
  
    1.  開啟 \[**While**\] 活動的捷徑功能表，然後選擇 \[**複製**\]。  在工作流程設計工具中，開啟\[**onWorkflowActivated1**\] 活動底下行的捷徑功能表，然後選取 \[**貼上**\]。  
  
    2.  從 \[**工具箱**\] 拖曳 \[**While**\] 活動至工作流程設計工具，然後將活動連接至 \[**onWorkflowActivated1**\] 活動底下的行。  
  
6.  選取 \[**WhileActivity1**\] 活動。  
  
7.  在 \[**屬性**\] 視窗中，將 \[**Condition**\] 設為 \[Code Condition\]。  
  
8.  展開 \[**Condition**\] 屬性，並於 \[**Condition**\] 子屬性旁輸入 isWorkflowPending，然後按下 ENTER 鍵。  
  
     \[程式碼編輯器\] 隨即開啟，而且名為 isWorkflowPending 的方法會加入至 Workflow1 程式碼檔中。  
  
9. 切換回工作流程設計工具，開啟工具箱，然後展開 \[**SharePoint 工作流程**\] 節點。  
  
10. 在 \[**工具箱**\] 的 \[**SharePoint Workflow**\] 節點，請執行下列其中一組步驟：  
  
    -   開啟 \[**OnWorkflowItemChanged**\] 活動的捷徑功能表，然後選擇 \[**複製**\]。  在工作流程設計工具中，開啟\[**whileActivity1**\] 活動中的行的捷徑功能表，然後選取 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 \[**OnWorkflowItemChanged**\] 活動至工作流程設計工具，然後將它連接至 \[**whileActivity1**\] 活動內的一行。  
  
11. 選取 \[**onWorkflowItemChanged1**\] 活動。  
  
12. 在 \[**屬性**\] 視窗中，依照下表所示設定屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## 處理活動事件  
 最後，檢查每一個活動的文件狀態。  如果文件已經過檢視，工作流程就會結束。  
  
#### 處理活動事件  
  
1.  在 Workflow1.cs 或 Workflow1.vb 中，將下列欄位加入至 \[`Workflow1`\] 類別頂端。  活動中會使用這個欄位判斷工作流程是否已結束。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  將下列方法加入至 `Workflow1` 類別。  這個方法會檢查 \[文件\] 清單的 `Document Status` 屬性值，判斷文件是否已經過檢視。  如果 `Document Status` 屬性設為 `Review Complete`，則 `checkStatus` 方法會將 `workflowPending` 欄位設為 **false**，表示工作流程已準備結束。  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  將下列程式碼加入至 `onWorkflowActivated`，並且加入 `onWorkflowItemChanged` 方法呼叫 `checkStatus` 方法。  工作流程開始時，`onWorkflowActivated` 方法會呼叫 `checkStatus` 方法，判斷文件是否已經過檢視。  如果文件尚未檢視，則工作流程會繼續。  文件儲存時，`onWorkflowItemChanged` 方法會再次呼叫 `checkStatus` 方法，判斷文件是否已經過檢視。  `workflowPending` 欄位設為 **true** 時，工作流程會繼續執行。  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  將下列程式碼加入至 `isWorkflowPending` 方法，以便檢查 `workflowPending` 屬性的狀態。  每次儲存文件時，**whileActivity1** 活動都會呼叫 `isWorkflowPending` 方法。  這個方法會檢查 <xref:System.Workflow.Activities.ConditionalEventArgs> 物件的 <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> 屬性，判斷 **WhileActivity1** 活動應繼續或結束。  如果屬性設為 **true**，則活動會繼續。  否則活動會結束，作業流程也會結束。  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  儲存專案。  
  
## 測試 SharePoint 工作流程範本  
 當您啟動偵錯工具時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將工作流程範本部署至 SharePoint 伺服器，並且建立工作流程與 \[**共用文件**\] 清單之間的關聯。  若要測試工作流程，請從 \[**共用文件**\] 清單中的某個文件啟動工作流程的執行個體。  
  
#### 測試 SharePoint 工作流程範本  
  
1.  在 Workflow1.cs 或 Workflow1.vb 中，設定 \[**onWorkflowActivated**\] 方法旁的中斷點。  
  
2.  選擇 F5 鍵以建置和執行方案。  
  
     SharePoint 網站隨即出現。  
  
3.  在 SharePoint 的巡覽窗格中按一下 \[**共用文件**\] 連結。  
  
4.  在 \[**共用文件**\] 頁面中，按一下 \[**程式庫工具**\] 索引標籤上的 \[**文件**\] 連結，然後按一下 \[**上載文件**\] 按鈕。  
  
5.  在 \[**上載文件**\] 對話方塊中，選取 \[**瀏覽**\] 按鈕，選取任何檔案，選擇 \[**開啟**\] 按鈕，然後選擇 \[**確定**\] 按鈕。  
  
     這樣做會將選取的文件上載至 \[**共用文件**\] 清單並啟動工作流程。  
  
6.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，確認偵錯工具在 `onWorkflowActivated` 方法旁的中斷點處停止。  
  
7.  選擇 F5 鍵繼續執行。  
  
8.  您可以在此變更文件的設定，但請先按一下 \[**儲存**\] 按鈕，保留目前的預設值。  
  
     這會返回預設 SharePoint 網站的 \[**共用文件**\] 頁面。  
  
9. 在 \[**共用文件**\] 頁面中，確認 \[**MySharePointWorkflow – Workflow1**\] 資料行下方的值設為 \[**進行中**\]。  這表示工作流程正在進行，且文件正在等候檢視。  
  
10. 在 \[**共用文件**\] 頁面中，選取文件，選擇顯示的箭號，然後選取 \[**編輯屬性**\] 功能表項目。  
  
11. 將 \[**文件狀態**\] 設為 \[**檢視完成**\]，然後按一下 \[**儲存**\] 按鈕。  
  
     這會返回預設 SharePoint 網站的 \[**共用文件**\] 頁面。  
  
12. 在 \[**共用文件**\] 頁面中，確認 \[**文件狀態**\] 資料行下方的值設為 \[**檢視完成**\]。  重新整理 \[**共用文件**\] 頁面並確認 \[**MySharePointWorkflow – Workflow1**\] 資料行下方的值設為 \[**檢視完成**\]。  這表示工作流程已結束，且文件已經過檢視。  
  
## 後續步驟  
 您可以在下列主題中，進一步了解如何建立工作流程範本：  
  
-   若要進一步了解 SharePoint 工作流程活動，請參閱 [SharePoint Foundation 的工作流程活動](http://go.microsoft.com/fwlink/?LinkId=178992)。  
  
-   若要進一步了解 Windows Workflow Foundation 活動，請參閱 [System.Workflow.Activities 命名空間](http://go.microsoft.com/fwlink/?LinkId=178993)。  
  
## 請參閱  
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  