---
title: "逐步解說：使用關聯與初始化表單建立工作流程"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "關聯表單 [Visual Studio 中的 SharePoint 開發]"
  - "初始表單 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 工作流程關聯表單"
  - "Visual Studio 中的 SharePoint 開發, 工作流程初始表單"
  - "Visual Studio 中的 SharePoint 開發, 工作流程"
  - "工作流程 [Visual Studio 中的 SharePoint 開發]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：使用關聯與初始化表單建立工作流程
  本逐步解說示範如何建立結合使用關聯與初始表單的基本循序工作流程。  這些是 ASPX 表單，可在 SharePoint 系統管理員最初建立工作流程的關聯 \(關聯表單\)，以及在使用者啟動工作流程 \(初始表單\) 時，將參數加入至工作流程。  
  
 本逐步解說將針對案例進行概要說明，在這個案例中，使用者想建立費用報表的核准工作流程，此工作流程的需求如下：  
  
-   當工作流程與清單產生關聯時，系統會將關聯表單提示給系統管理員看到，讓他們輸入費用報表的金額限制。  
  
-   員工將他們的費用報表上載至共用文件清單、啟動工作流程，然後在工作流程初始表單中輸入費用總支出。  
  
-   如果員工的費用報表總支出超過系統管理員預先定義的限制，系統會建立工作給員工的主管，以核准費用報表。  不過，如果員工的費用報表總支出低於或等於費用限制，就會將自動核准的訊息寫入工作流程的歷程清單。  
  
 這個逐步解說將說明下列工作：  
  
-   在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立 SharePoint 清單定義循序工作流程專案。  
  
-   建立工作流程排程。  
  
-   處理工作流程活動事件。  
  
-   建立工作流程關聯和初始表單。  
  
-   與工作流程建立關聯。  
  
-   手動啟動工作流程。  
  
> [!NOTE]  
>  雖然本逐步解說使用循序工作流程專案，但狀態機器工作流程的程序完全相同。  
>   
>  此外，在下列指示的某些 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。  您所擁有的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 建立 SharePoint 循序工作流程專案  
 首先，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立循序工作流程專案。  循序工作流程是依順序執行直到最後一個活動完成為止的一系列步驟。  在此程序中，您將建立套用至 SharePoint 中共用文件清單的循序工作流程。  工作流程的精靈會讓您將工作流程與網站或清單定義加以關聯，並且讓您決定工作流程將在何時啟動。  
  
#### 建立 SharePoint 循序工作流程專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  在 \[**範本**\] 窗格中，選取 \[**SharePoint 2010 專案**\] 專案範本。  
  
4.  在 \[**名稱**\] 文字方塊中，輸入 ExpenseReport，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
5.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕，以接受信任層級和預設網頁。  
  
     此步驟也會將方案的信任層級設定為陣列方案，這是工作流程專案唯一可用的選項。  
  
6.  在 \[**方案總管**\] 中選擇專案節點。  
  
7.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
8.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
9. 在 \[**範本**\] 窗格中，選取 \[**循序工作流程 \(僅限陣列方案\)**\] 範本，然後選擇 \[**加入**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
10. 在 \[**指定工作流程名稱進行偵錯**\] 頁面中，接受預設名稱 \(**ExpenseReport \- Workflow1**\)。  保留預設工作流程範本類型值 \(\[**清單工作流程**\]\)。  選擇 \[**下一步**\] 按鈕。  
  
11. 在 \[**您要 Visual Studio 在偵錯工作階段中自動關聯工作流程嗎?**\] 頁面中，清除它自動關聯工作流程範本的方塊 \(如果已經核取的話\)。  
  
     此步驟可讓您稍後在顯示關聯表單時，手動建立工作流程與共用文件清單的關聯。  
  
12. 選擇 \[**完成**\] 按鈕。  
  
## 將關聯表單加入至工作流程  
 接下來，建立 .ASPX 關聯表單，這個表單會在 SharePoint 系統管理員一開始建立工作流程與費用報表文件的關聯時出現。  
  
#### 若要將關聯表單加入至工作流程  
  
1.  在 \[**方案總管**\] 中，選擇 \[**Workflow1**\] 節點。  
  
2.  在功能列表上選擇 \[**專案**\]、\[**加入新項目**\]，顯示 \[**加入新項目**\] 對話方塊。  
  
3.  在對話方塊樹狀檢視中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] \(視專案語言而定\)，然後展開 \[**SharePoint**\] 節點，再按一下 \[**2010**\] 節點。  
  
4.  在範本清單中，選取 \[**工作流程關聯表單**\] 範本。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 ExpenseReportAssocForm.aspx。  
  
6.  按一下 \[**加入**\] 按鈕，將表單加入至專案。  
  
## 設計和撰寫關聯表單的程式碼  
 在這個程序中，您會將控制項和程式碼加入至關聯表單來增加功能。  
  
#### 若要設計和撰寫關聯表單的程式碼  
  
1.  在關聯表單 \(ExpenseReportAssocForm.aspx\) 中找到具有 `ID="Main"` 的 `asp:Content` 項目。  
  
2.  直接在此內容項目的第一行後面，加入下列程式碼來建立標籤和文字方塊，以提示輸入費用核准限制 \(*AutoApproveLimit*\)：  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  在 \[**方案總管**\] 中展開 \[**ExpenseReportAssocForm.aspx**\] 檔案，以顯示其相依檔案。  
  
    > [!NOTE]  
    >  如果您的專案位於 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]，您必須按一下 \[**檢視所有檔案**\] 按鈕來執行此步驟。  
  
4.  開啟 ExpenseReportAssocForm.aspx 檔案的捷徑功能表並選擇 \[**檢視程式碼**\]。  
  
5.  以下列方法取代 `GetAssociationData` 方法：  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## 將初始表單加入至工作流程  
 接下來，建立初始表單，這個表單會在使用者執行工作流程來處理費用報表時出現。  
  
#### 若要建立初始表單  
  
1.  在 \[**方案總管**\] 中，選擇 \[**Workflow1**\] 節點。  
  
2.  按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]，顯示 \[**加入新項目**\] 對話方塊。  
  
3.  在對話方塊樹狀檢視中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] \(視專案語言而定\)，然後展開 \[**SharePoint**\] 節點，再按一下 \[**2010**\] 節點。  
  
4.  在範本清單中，選取 \[**工作流程初始表單**\] 範本。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 ExpenseReportInitForm.aspx。  
  
6.  按一下 \[**加入**\] 按鈕，將表單加入至專案。  
  
## 設計和撰寫初始表單的程式碼  
 接下來，將控制項和程式碼加入至初始表單來增加功能。  
  
#### 若要撰寫初始表單的程式碼  
  
1.  在初始表單 \(ExpenseReportInitForm.aspx\) 中找出包含 `ID="Main"` 的 `asp:Content` 項目。  
  
2.  直接在此內容項目的第一行後面，加入下列程式碼來建立標籤和文字方塊，以顯示關聯表單中輸入的費用核准限制 \(*AutoApproveLimit*\) 標籤和文字方塊，然後建立另一個標籤和文字方塊，以提示輸入總支出 \(*ExpenseTotal*\)：  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  在 \[**方案總管**\] 中展開 \[**ExpenseReportInitForm.aspx**\] 檔案，以顯示其相依檔案。  
  
4.  開啟 ExpenseReportInitForm.aspx 檔案的捷徑功能表並選擇 \[**檢視程式碼**\]。  
  
5.  以下列範例取代 `Page_Load` 方法：  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  以下列範例取代 `GetInitiationData` 方法：  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## 自訂工作流程  
 接下來，自訂工作流程。  您稍後會建立兩個表單與工作流程的關聯。  
  
#### 若要自訂工作流程  
  
1.  開啟專案中的 \[Workflow1\]，在工作流程設計工具中顯示工作流程。  
  
2.  在 \[**工具箱**\] 中，展開 \[**Windows Workflow v3.0**\] 節點並找出 \[**IfElse**\] 活動。  
  
3.  執行下列其中一項步驟，將此活動加入至工作流程：  
  
    -   開啟 \[**IfElse**\] 活動的捷徑功能表，選擇 \[**複製**\]，開啟 \[**onWorkflowActivated1**\] 活動底下那一行的捷徑功能表，然後選擇 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 \[**IfElse**\] 活動，然後將它連接至工作流程設計工具中 \[**onWorkflowActivated1**\] 活動底下一行。  
  
4.  在 \[工具箱\] 中，展開 \[**SharePoint 工作流程**\] 節點並找出 \[**CreateTask**\] 活動。  
  
5.  執行下列其中一項步驟，將此活動加入至工作流程：  
  
    -   開啟 \[**CreateTask**\] 活動的捷徑功能表，選擇 \[**複製**\]，開啟工作流程設計工具中，IfElseActivity1 內的兩個 \[**放置活動於此**\] 的捷徑功能表，然後選取 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 \[**CreateTask**\] 活動至 IfElseActivity1 內的兩個 \[**此處置放活動**\] 區域之一上。  
  
6.  在 \[**屬性**\] 視窗中，為 **CorrelationToken** 屬性輸入 *taskToken* 屬性值。  
  
7.  按一下 **CorrelationToken** 屬性旁的加號 \(![TreeView 加號](~/docs/sharepoint/media/plus.gif "TreeView 加號")\) 來展開它。  
  
8.  選取 **OwnerActivityName** 子屬性的下拉箭號，並設定 *Workflow1* 值。  
  
9. 按一下 \[**TaskId**\] 屬性，然後按一下省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\) 按鈕以顯示 \[**繫結屬性**\] 對話方塊。  
  
10. 選取 \[**繫結至新的成員**\] 索引標籤，選取 \[**建立欄位**\] 選項按鈕，然後選擇 \[**確定**\] 按鈕。  
  
11. 按一下 \[**TaskProperties**\] 屬性，然後按一下省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\) 按鈕以顯示 \[**繫結屬性**\] 對話方塊。  
  
12. 選取 \[**繫結至新的成員**\] 索引標籤，選取 \[**建立欄位**\] 選項按鈕，然後選擇 \[**確定**\] 按鈕。  
  
13. 在 \[**工具箱**\] 中，展開 \[**SharePoint 工作流程**\] 節點並找出 \[**LogToHistoryListActivity**\] 活動。  
  
14. 執行下列其中一項步驟，將此活動加入至工作流程：  
  
    -   開啟 \[**LogToHistoryListActivity**\] 活動的捷徑功能表，選擇 \[**複製**\]，開啟工作流程設計工具中，IfElseActivity1 內的另一個 \[**放置活動於此**\] 的捷徑功能表，然後選取 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 \[**LogToHistoryListActivity**\] 活動，然後拖放至 IfElseActivity1 內的另一個 \[**此處置放活動**\] 區域。  
  
## 將程式碼加入至工作流程  
 接下來，將程式碼加入至工作流程來增加功能。  
  
#### 若要將程式碼加入工作流程  
  
1.  在工作流程設計工具開啟 \[**createTask1**\] 活動的捷徑功能表，然後選取 \[**檢視程式碼**\]。  
  
2.  加入下列方法：  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  在程式碼中，以將建立工作的網域和使用者取代 `somedomain\\someuser`，例如 "`Office\\JoeSch`"。  為了進行測試，使用開發用的帳戶會比較方便。  
  
3.  在 `MethodInvoking` 方法之下加入下列範例：  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  在工作流程設計工具中，按一下 \[**ifElseBranchActivity1**\] 活動。  
  
5.  在 \[**屬性**\] 視窗中，按一下 \[**條件**\] 屬性的下拉箭號，然後設定 \[*Code Condition*\] 值。  
  
6.  按一下 \[**條件**\] 屬性旁的加號 \(![TreeView 加號](~/docs/sharepoint/media/plus.gif "TreeView 加號")\) 來展開它，然後將其值設定為 \[*checkApprovalNeeded*\]。  
  
7.  在工作流程設計工具中，開啟 \[**logToHistoryListActivity1**\] 活動的捷徑功能表，然後選取 \[**產生處理常式**\]，為 `MethodInvoking` 事件產生空方法。  
  
8.  以下列程式碼取代 `MethodInvoking` 程式碼：  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. 按 F5 鍵偵錯程式。  
  
     這會編譯、封裝、部署應用程式、啟動其功能、回收 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區，然後在 \[**網站 URL**\] 屬性指定的位置啟動瀏覽器。  
  
## 建立工作流程與文件清單的關聯  
 接下來，建立工作流程與 SharePoint 網站上的 \[**共用文件**\] 清單的關聯，以顯示工作流程關聯表單。  
  
#### 若要關聯工作流程  
  
1.  按一下快速啟動列上的 \[**共用文件**\] 連結。  
  
2.  按一下 \[**程式庫工具**\] 索引標籤上的 \[**程式庫**\] 連結，然後按一下 \[**程式庫設定**\] 功能區按鈕。  
  
3.  在 \[**權限與管理**\] 區段中，按一下 \[**工作流程設定**\] 連結，然後按 \[**工作流程**\] 頁面上的 \[**加入工作流程**\] 連結。  
  
4.  在工作流程設定頁面的上方清單中，選取 \[**ExpenseReport \- Workflow1**\] 範本。  
  
5.  在下一個欄位中，輸入 ExpenseReportWorkflow，然後按 \[**下一步**\] 按鈕。  
  
     這會建立工作流程與 \[**共用文件**\] 清單的關聯，並顯示工作流程關聯表單。  
  
6.  在 \[**自動核准限制**\] 文字方塊中，輸入 1200，然後按一下 \[**關聯工作流程**\] 按鈕。  
  
## 啟動工作流程  
 接下來，建立工作流程與 \[**共用文件**\] 清單中其中一個文件的關聯，以顯示工作流程初始表單。  
  
#### 若要啟動工作流程  
  
1.  在 SharePoint 頁面上，選擇 \[**首頁**\] 按鈕。  
  
2.  按下在快速啟動列上的 \[**共用文件**\] 連結，顯示 \[**共用文件**\] 清單。  
  
3.  在頁面頂端按一下 \[**程式庫工具**\] 索引標籤上的 \[**文件**\] 連結，然後按一下功能區上的 \[**上載文件**\] 按鈕，將新文件上載至 \[**共用文件**\] 清單。  
  
4.  在 \[**上載文件**\] 對話方塊中，選取 \[**瀏覽**\] 按鈕，選取任何檔案，選擇 \[**開啟**\] 按鈕，然後選擇 \[**確定**\] 按鈕。  
  
     您可以在這個對話方塊中變更文件的設定，但請先按一下 \[**儲存**\] 按鈕，保留目前的預設值。  
  
5.  選取上載的文件，選取要顯示的下拉箭號，然後選取 \[**工作流程**\] 項目。  
  
6.  按一下 ExpenseReportWorkflow 旁的影像。  
  
     這會顯示工作流程初始表單 \(請注意，\[**自動核准限制**\] 方塊中顯示的值是唯讀的，因為此值是在關聯表單中輸入的\)。  
  
7.  在 \[**費用總支出**\] 文字方塊中，輸入 1600，然後選擇 \[**啟動工作流程**\] 按鈕。  
  
     這會再次顯示 \[**共用文件**\] 清單。  名為 \[**ExpenseReportWorkflow**\] 的新欄和值 \[**已完成**\] 會加入至工作流程剛才啟動的項目中。  
  
8.  按一下上載的文件旁的下拉箭號，然後按一下 \[**工作流程**\] 來顯示工作流程狀態頁面。  按一下 \[**完成的工作流程**\] 底下的 \[**已完成**\] 值。  工作會列在 \[**工作**\] 區段底下。  
  
9. 按一下工作的標題來顯示工作詳細資訊。  
  
10. 回到 \[**共用文件**\] 清單，然後使用相同或不同文件重新啟動工作流程。  
  
11. 在初始頁面上輸入金額，此金額小於或等於關聯頁面上輸入的金額 \(1200\)。  
  
     這時會在歷程清單中建立項目，而非建立工作。  此項目會顯示在工作流程狀態頁面的 \[**工作流程記錄**\] 區段中。  請注意記錄事件的 \[**結果**\] 欄中的訊息。  它包含 `logToHistoryListActivity1.MethodInvoking` 事件中輸入的文字，其中包括自動核准的金額。  
  
## 後續步驟  
 您可以在下列主題中，進一步了解如何建立工作流程範本：  
  
-   若要進一步了解 SharePoint 工作流程，請參閱 [Windows SharePoint Services 的工作流程](http://go.microsoft.com/fwlink/?LinkID=166275)。  
  
## 請參閱  
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [逐步解說：將應用程式頁面新增到工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  