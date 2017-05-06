---
title: "逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio"
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
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 程式開發，匯入可重複使用的工作流程"
  - "可重複使用的工作流程 [Visual Studio 中的 SharePoint 程式開發]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio
  本逐步解說示範如何將 SharePoint Designer 2010 中建立的可重複使用的工作流程匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 工作流程專案。  
  
 SharePoint Designer 中建立的工作流程或「*宣告式工作流程*」\(Declarative Workflow\) 是由 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 陳述式組成，而非程式碼所組成。  SharePoint Designer 2010 新增了「*可重複使用的工作流程*」\(Reusable Workflow\)，這是可移植的宣告式工作流程，可供 SharePoint 網站中的不同清單使用。  
  
 在 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 中建立的工作流程 \(例如循序和狀態機器工作流程\) 稱為「*程式碼工作流程*」\(Code Workflow\)。  程式碼工作流程由 XML 檔案和程式碼模組所組成，使用者可以在其中自訂工作流程的行為。  
  
 Visual Studio 讓您可匯入 SharePoint Designer 2010 中建立的可重複使用的工作流程，並將它們轉換成程式碼工作流程，以便在 SharePoint 網站中使用。  
  
 本逐步解說將示範下列工作：  
  
-   在 SharePoint Designer 中建立可重複使用的簡單工作流程。  
  
-   將 SharePoint Designer 可重複使用的工作流程匯出至 .wsp 檔案和 SharePoint 中。  
  
-   使用「匯入可重複使用的工作流程」專案，將 .wsp 檔案匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   加入程式碼來變更工作流程。  
  
-   在 SharePoint 網站中使用匯入的工作流程。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## 建立目標 SharePoint 子網站  
 首先，您會建立兩個新的 SharePoint 子網站，一個用來裝載 SharePoint Designer 建立的可重複使用的工作流程，另一個用來裝載轉換後的工作流程。  
  
#### 若要建立 SharePoint 子網站  
  
1.  在 SharePoint Designer 2010 中，功能表列上，選擇 \[**檔案**\]、\[**新的空白網站**\]。  
  
2.  在 \[**開啟網站**\] 對話方塊中，瀏覽至您要建立工作流程的 SharePoint 網站，或使用值 http:\/\/*SystemName*\/，然後按一下 \[**確定**\] 按鈕。  
  
     首頁隨即出現。  
  
3.  在 \[**Subsites**\] 區段中，選擇 \[**新增**\] 按鈕。  
  
4.  在 \[**新增**\] 對話方塊，請在清單的左窗格選擇 \[**SharePoint 範本**\] ，然後在清單的右窗格選擇 \[**小組網站**\] 。  
  
5.  在 \[**指定網站位置**\] 方塊中，將 URL 中的 **subsite** 一字取代成 SPD1，然後按一下 \[**確定**\] 按鈕。  
  
     這會在 SharePoint Designer 中開啟新的子網站。  關閉這個 SharePoint Designer 執行個體，然後回到第一個執行個體 \(最上層網站\)。  
  
6.  重複步驟 3 \- 5 來建立第二個子網站，這次將 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 中的 **subsite** 一字取代成 SPD2。  
  
## 建立 SharePoint Designer 可重複使用的工作流程  
 由於 SharePoint 並未隨附任何可重複使用的工作流程可供這個範例使用，因此您將建立一個可重複使用的工作流程。  在這個簡單的工作流程中，當使用者在 \[工作\] 清單中輸入具有特定標題的新工作時，工作就會指派給該使用者。  
  
#### 若要建立 SharePoint Designer 可重複使用的工作流程  
  
1.  在 \[**子網站**\] 區段中，選擇 \[**SPD1**\] 網站來修改它。  
  
2.  在功能區上，請選擇 \[**可重複使用的工作流程**\] 按鈕。  
  
     \[建立可重複使用的工作流程\] 精靈隨即出現。  
  
3.  在 \[**名稱**\] 方塊中輸入「SPD Task Workflow」。  
  
4.  在 \[**內容類型**\] 清單中，選擇 \[**Task**\]，然後選擇 \[**確定**\] 按鈕。  
  
     工作流程隨即在 SharePoint Designer 工作流程設計工具中開啟。  
  
5.  在工作流程設計工具中，選取 Step 1，然後在功能區上選擇 \[**條件**\] 按鈕。  
  
6.  在條件清單中，選取 \[**如果目前項目欄位等於值**\]。  
  
     這個步驟會加入名為 \[**如果等於欄位值**\] 的情況。  
  
7.  在 \[**如果欄位等於值**\] 條件中，選擇 \[**欄位**\] 連結。  
  
8.  在值清單中，選取 \[**標題**\]。  
  
9. 在 \[**如果欄位等於值**\] 條件中，選擇 \[**值**\] 連結。  
  
10. 在方塊中輸入新工作。  
  
     條件陳述式現在會顯示 \[**如果目前項目: 標題等於新工作**\]。  
  
11. 選取在條件陳述式下的行，接著在功能區上，選擇 \[**動作**\] 按鈕。  
  
12. 在動作清單中，選取 \[**設定目前項目的欄位**\]。  
  
13. 在 \[**將欄位設成值**\] 動作中，選取 \[**欄位**\] 連結，然後在清單中選取 \[**指派給**\]。  
  
14. 在 \[**設定欄位值**\] 動作，選擇 \[**值**\] 連結，然後，在現有的使用者以及群組清單，選取 \[**建立項目的使用者**\]。  
  
15. 選擇 \[**新增**\] 按鈕，然後選擇 \[**確定**\] 按鈕。  
  
     動作陳述式現在會顯示 \[**將指派給設成目前項目:CreatedBy**\]。  
  
## 儲存和部署可重複使用的工作流程  
 由於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只能匯入 .wsp 檔案，因此您必須先將可重複使用的工作流程另存為 .wsp 檔案，並將其部署至 SharePoint，然後才能將其匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  
  
> [!IMPORTANT]  
>  如果您在執行下列程序時收到執行階段錯誤，表示必須在可存取 SharePoint 網站的系統上執行程序。  
  
#### 若要儲存和部署可重複使用的工作流程  
  
1.  按一下 SharePoint Designer 頂端的 \[**儲存**\] 按鈕來儲存進度，然後按一下 \[**發行**\] 按鈕，將工作流程部署至 \[**SPD1**\] SharePoint 網站。  
  
2.  在巡覽窗格中，選取 \[**工作流程**\] 物件。  
  
3.  在 \[**可重複使用的工作流程**\] 中，選擇 \[**SPD 工作流程**\]。  
  
4.  按一下功能區上的 \[**另存範本**\] 按鈕，將工作流程儲存為 .wsp 檔案。  
  
5.  在瀏覽器中開啟 \[**SPD1**\] 這個 SharePoint 網站，以在 SharePoint 中檢視 .wsp 檔案。  
  
6.  在快速啟動列，請選擇 \[**程式庫**\] 連結。  
  
7.  按一下 \[**文件庫**\] 區段中的 \[**網站資產**\] 連結。  
  
     \[**SPD 工作工作流程**\] 檔案會與其他網站資產一起列出。  
  
8.  在檔案清單中，選取該檔案名稱  
  
9. 按一下 \[**檔案下載**\] 對話方塊中的 \[**儲存**\] 按鈕，以將 .wsp 檔案儲存在本機系統上。  
  
## 將 .wsp 檔案匯入 Visual Studio  
 使用 \[匯入可重複使用的工作流程\] 專案，將 .wsp 檔案匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  此專案會將工作流程從可重複使用的宣告式工作流程轉換成程式碼工作流程。  轉換工作流程之後，您將使用程式碼來修改其行為。  
  
#### 若要從 .wsp 檔案匯入工作流程並加以修改  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  在 \[**範本**\] 窗格中，選取 \[**匯入可重複使用的 SharePoint 2010 工作流程**\] 範本，將專案名稱保留為 \[**WorkflowImportProject1**\]，然後選擇 \[**確定**\] 按鈕。  
  
     \[SharePoint 自訂精靈\] 隨即出現。  
  
4.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，輸入您在先前建立之第二個 SharePoint 子網站的 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]：http:\/\/*system name*\/SPD2。  
  
5.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，選擇 \[**部署為陣列方案**\] 選項按鈕，然後按 \[**下一步**\] 按鈕。  
  
     如需沙箱化方案與陣列方案的比較的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  在 \[**指定新專案來源**\] 頁面中，瀏覽至您先前在系統上儲存 .wsp 檔案的位置，然後按 \[**下一步**\] 按鈕。  
  
    > [!NOTE]  
    >  選擇 \[**結束**\] 按鈕會匯入 .wsp 檔案中所有可用的項目。  
  
     如此會顯示可供匯入的可重複使用工作流程清單。  
  
7.  在 \[**選取要匯入的項目**\] 方塊中，選取工作流程 \[**SPD 工作工作流程**\]，然後按一下 \[**完成**\] 按鈕。  
  
     完成匯入作業後，系統會建立名為 \[**WorkflowImportProject1**\] 的專案，其中包含名為 \[**SPD\_Workflow\_TestFT**\] 的工作流程。  此資料夾包含工作流程的定義檔 Elements.xml 以及工作流程設計工具檔案 \(.xoml\)。  設計工具包含兩個檔案：規則檔 \(.rules\) 和程式碼後置檔案 \(.cs 或 .vb，視專案的程式語言而定\)。  
  
8.  在 \[**方案總管**\] 中，刪除 \[**其他匯入的檔案**\] 資料夾。  
  
9. 在 Elements.xml 檔案中，刪除 `InstantiationURL="_layouts/IniErkflIP.sspx"`。  
  
10. 在 \[**方案總管**\] 中，選取 \[**WorkflowImportProject1**\]，然後在功能表列上，選擇 \[**專案**\]、 \[**做為啟始專案**\] ，將 \[**WorkflowImportProject1**\] 設定為啟始項目。  
  
     如此會在偵錯專案時立即顯示清單。  
  
11. 因為 \[**匯入可重複使用的 SharePoint 2010 工作流程**\] 範本不會匯入已匯入工作流程的關聯屬性值，所以必須由您輸入。  如要完成這項工作：  
  
    1.  在 \[**方案總管**\] 中，選擇 \[**SPD\_Workflow\_TestFT**\] 節點。  
  
    2.  在其中一個清單屬性選取旁邊的省略符號 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\) 按鈕，例如 \[**目標清單**\] 屬性。  
  
    3.  填入 SharePoint 自訂精靈中未填入的值，然後選擇 \[**結束**\] 按鈕。  
  
12. 選取 .xoml 檔案，然後在功能表列上，選擇 \[**檢視**\]、\[**設計工具**\]，檢視在工作流程設計工具中匯入的工作流程。  
  
13. 在 \[**工具箱**\] 的 \[**Windows Workflow v3.0**\] 節點，請執行下列其中一個步驟：  
  
    -   開啟 \[**程式碼**\] 活動的捷徑功能表，然後選擇 \[**複製**\]。  在工作流程設計工具中，開啟\[**SequenceActivity1**\] 活動底下行的捷徑功能表，然後選取 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 \[**程式碼**\] 活動至工作流程設計工具，並將它連接至 \[**SequenceActivity1**\] 活動底下的行。  
  
     這會將名為 \[**CodeActivity1**\] 的活動加入至工作流程設計工具。  在此活動中，您將加入程式碼動作，此程式碼動作會在使用者啟動工作流程時，在 \[公告\] 清單中建立公告。  
  
14. 請執行下列其中一組步驟：  
  
    -   按兩下 \[**CodeActivity1**\]，產生事件處理常式並檢視程式碼。  
  
    -   在 \[**CodeActivity1**\] 的 \[**屬性**\] 視窗中，將 \[**ExecuteCode**\] 屬性值設定為 \[**codeActivity\_ExecuteCode**\]。  
  
15. 將下列程式碼加入至現有 **using** 或 **Imports** 陳述式底下：  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 以下列程式碼取代 `codeActivity1_ExecuteCode`：  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## 部署專案並建立工作流程關聯  
 接下來，執行 WorkflowImportProject1 以將它部署至 SharePoint 網站，然後將工作流程與 \[工作\] 清單相關聯，以檢視和測試修改和轉換後的工作流程。  
  
#### 若要部署專案並建立工作流程關聯  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，按 F5 鍵執行和部署轉換後的工作流程專案。  
  
2.  按一下快速啟動列上的 \[**工作**\] 連結，顯示 \[工作\] 清單。  
  
3.  在 \[**清單工具**\] 索引標籤上，選擇 \[**項目**\] 按鈕，然後選擇 \[**新的項目**\] 按鈕。  
  
     \[**工作 \- 新項目**\] 對話方塊隨即開啟。  
  
4.  在 \[**標題**\] 方塊中，輸入 New task，然後選擇 \[**儲存**\] 按鈕。  
  
5.  在 \[**清單工具**\] 索引標籤上，選擇 \[**清單**\] 按鈕，然後選擇 \[**清單設定**\] 按鈕。  
  
     \[**清單設定**\] 頁面隨即出現。  
  
6.  按一下 \[**權限與管理**\] 區段中的 \[**工作流程設定**\] 連結。  
  
     \[**工作流程設定**\] 頁面隨即出現。  
  
7.  選擇 \[**加入工作流程**\] 連結。  
  
8.  在 \[**工作流程**\] 清單中，選取 \[**WorkflowImportProject1 \- SPD 工作流程測試**\]。  
  
9. 在 \[**名稱**\] 方塊中，輸入 SPD Workflow Test，然後選擇 \[**確定**\] 按鈕。  
  
10. 在快速啟動列上，選取 \[**工作**\] 清單。  
  
11. 選取 \[**新的工作**\] 旁邊的箭號，然後在清單中選取 \[**工作流程**\]。  
  
12. 選取 \[**開始新的工作流程**\] 區段中的 \[**SPD 工作流程**\] 的連結，然後按 \[**開始**\] 按鈕，初始化工作流程。  
  
    > [!NOTE]  
    >  或者，您也可以執行工作流程設定精靈並設定工作流程自動產生關聯，以自動產生工作流程與清單之間的關聯。  
  
     請注意，工作流程會執行兩個動作：您的名稱出現在工作的 \[**指派給**\] 資料行中，而公告出現在 \[**公告**\] 清單中。  
  
## 請參閱  
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  