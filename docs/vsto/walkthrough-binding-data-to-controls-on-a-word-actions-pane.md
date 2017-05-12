---
title: "逐步解說：在 Word 執行窗格將資料繫結至控制項"
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
  - "動作窗格 [Visual Studio 中的 Office 程式開發], 繫結控制項"
  - "動作窗格 [Visual Studio 中的 Office 程式開發], 資料繫結"
  - "控制項 [Visual Studio 中的 Office 程式開發], 資料繫結"
  - "資料繫結 [Visual Studio 中的 Office 程式開發], 執行窗格"
  - "資料繫結 [Visual Studio 中的 Office 程式開發], 智慧文件"
  - "智慧文件 [Visual Studio 中的 Office 程式開發], 資料繫結"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# 逐步解說：在 Word 執行窗格將資料繫結至控制項
  本逐步解說提供在執行窗格上的控制項示範如何將資料繫結至文字。  控制項示範 SQL Server 資料庫中資料表之間的主從式關聯。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立執行窗格，這個執行窗格包含繫結至資料的 Windows Form 控制項。  
  
-   使用主從式關聯性顯示控制項中的資料。  
  
-   在應用程式開啟時顯示執行窗格  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   與具有 Northwind SQL Server 範例資料庫之伺服器的連線。  
  
-   從 SQL Server 資料庫讀取及寫入該資料庫的使用權限。  
  
## 建立專案  
 第一步就是建立 Word 文件專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 My Word Actions Pane 的 Word 文件專案。  在精靈中選取 \[**建立新文件**\]。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 \[**My Word Actions Pane**\] 專案加入至 \[**方案總管**\]。  
  
## 將控制項加入至執行窗格  
 對於這個逐步解說，您需要包含資料繫結 Windows Form 控制項的執行窗格控制項。  將資料來源加入至專案，然後從 \[**資料來源**\] 視窗將控制項拖曳至執行窗格控制項。  
  
#### 若要加入執行窗格控制項  
  
1.  在 \[**方案總管**\] 中選取 \[**My Word Actions Pane**\] 專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，選取 \[**執行窗格控制項**\]，將其命名為 **ActionsControl**，然後按一下 \[**加入**\]。  
  
#### 若要將資料來源加入至專案  
  
1.  如果 \[**資料來源**\] 視窗中不可見，請顯示它，請在功能表列上，選擇 \[**檢視**\]\]，則 \[**其他視窗**\]， \[**資料來源**\]。  
  
    > [!NOTE]  
    >  如果無法使用 \[**顯示資料來源**\]，請按一下 Word 文件，然後再檢查一次。  
  
2.  按一下 \[**加入新資料來源**\]，啟動 \[**資料來源組態精靈**\]。  
  
3.  選取 \[**資料庫**\]，再按一下 \[**下一步**\]。  
  
4.  選取與 Northwind 範例 SQL Server 資料庫的資料連接，或使用 \[**新增連接**\] 按鈕加入新的連接。  
  
5.  按一下 \[**下一步**\]。  
  
6.  如果已經選取，請清除儲存連接的選項，然後按一下 \[**下一步**\]。  
  
7.  在 \[**資料庫物件**\] 視窗中，展開 \[**資料表**\] 節點。  
  
8.  選取 \[**供應商**\] 和 \[**產品**\] 資料表旁的核取方塊。  
  
9. 按一下 \[完成\]。  
  
 精靈會將 \[**供應商**\] 資料表和 \[**產品**\] 資料表加入至 \[**資料來源**\] 視窗，  也會將具型別資料集加入至 \[**方案總管**\] 中可以看得到的專案。  
  
#### 若要將資料繫結 Windows Form 控制項加入至執行窗格控制項  
  
1.  在 \[**資料來源**\] 視窗中，展開 \[**供應商**\] 資料表。  
  
2.  按一下 \[**公司名稱**\] 節點上的下拉箭號，並選取 \[**ComboBox**\]。  
  
3.  將 \[**CompanyName**\] 從 \[**資料來源**\] 視窗拖曳至執行窗格控制項。  
  
     在執行窗格控制項上會建立 <xref:System.Windows.Forms.ComboBox> 控制項。  同時，名為 `SuppliersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、資料表配接器和 <xref:System.Data.DataSet> 會加入至元件匣中的專案。  
  
4.  選取 \[**元件**\] 匣中的 `SuppliersBindingNavigator`，並按下 DELETE。  在這個逐步解說中，您不會使用 `SuppliersBindingNavigator`。  
  
    > [!NOTE]  
    >  刪除 `SuppliersBindingNavigator` 並不會移除為其產生的所有程式碼。  您可以移除此程式碼。  
  
5.  移動下拉式方塊，使其位於標籤底下，並將 \[**Size**\] 屬性變更為 171, 21。  
  
6.  在 \[**資料來源**\] 視窗中，展開屬於 \[**供應商**\] 資料表子系的 \[**產品**\] 資料表。  
  
7.  按一下 \[**ProductName**\] 節點上的下拉箭頭，並選取 \[**ListBox**\]。  
  
8.  將 \[**ProductName**\] 拖曳至執行窗格控制項。  
  
     在執行窗格控制項上會建立 <xref:System.Windows.Forms.ListBox> 控制項。  同時，名為 `ProductBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 和資料表配接器會加入至元件匣中的專案。  
  
9. 移動清單方塊，使其位於標籤之下，並將 \[**Size**\] 屬性變更為 171,95。  
  
10. 將 <xref:System.Windows.Forms.Button> 從 \[**工具箱**\] 拖曳至執行窗格控制項，並將其放置在清單方塊下方。  
  
11. 以滑鼠右鍵按一下 <xref:System.Windows.Forms.Button>，然後按一下捷徑功能表中的 \[**屬性**\]，再變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**Insert**|  
    |**文字**|**Insert**|  
  
12. 調整使用者控制項 \(User Control\) 的大小以符合控制項。  
  
## 設定資料來源  
 若要設定資料來源，請將程式碼加入至執行窗格控制項的 <xref:System.Windows.Forms.UserControl.Load> 事件，以用 <xref:System.Data.DataTable> 的資料填入控制項，並且設定每個控制項的 <xref:System.Windows.Forms.Binding.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性。  
  
#### 若要載入資料至控制項  
  
1.  在 `ActionsControl` 類別 \(Class\) 的 <xref:System.Windows.Forms.UserControl.Load> 事件處理常式中，加入下列程式碼。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  在 C\# 中，您必須將事件處理常式附加至 <xref:System.Windows.Forms.UserControl.Load> 事件。  您可以在呼叫 `InitializeComponent` 之後，將此程式碼放在 `ActionsControl` 建構函式中。  如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### 若要設定控制項的資料繫結屬性  
  
1.  選取 `CompanyNameComboBox` 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 \[**DataSource**\] 屬性右邊的按鈕，然後選取 \[**suppliersBindingSource**\]。  
  
3.  按一下 \[**DisplayMember**\] 屬性右邊的按鈕，然後選取 \[**CompanyName**\]。  
  
4.  展開 \[**DataBindings**\] 屬性，然後按一下 \[**Text**\] 屬性右邊的按鈕，再選取 \[**無**\]。  
  
5.  選取 `ProductNameListBox` 控制項。  
  
6.  在 \[**屬性**\] 視窗中，按一下 \[**DataSource**\] 屬性右邊的按鈕，然後選取 \[**productsBindingSource**\]。  
  
7.  按一下 \[**DisplayMember**\] 屬性右邊的按鈕，然後選取 \[**ProductName**\]。  
  
8.  展開 \[**DataBindings**\] 屬性，然後按一下 \[**SelectedValue**\] 屬性右邊的按鈕，再選取 \[**無**\]。  
  
## 加入方法以將資料插入資料表  
 下一個工作是從繫結控制項讀取資料，並用這些資料填入 \(Populate\) Word 文件中的資料表。  首先，建立將資料表標題格式化的程序，然後加入 `AddData` 方法以建立和格式化 Word 資料表。  
  
#### 若要格式化資料表標題  
  
1.  在 `ActionsControl` 類別中，建立格式化資料表標題的方法。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### 若要建立資料表  
  
1.  在 `ActionsControl` 類別中，如果資料表不存在時，請撰寫建立資料表的方法，然後將執行窗格中的資料加入至資料表。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### 若要將文字插入 Word 資料表  
  
1.  將下列程式碼加入至 \[**插入**\] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  在 C\# 中，您必須為按鈕的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  您可以將此程式碼放置在 `ActionsControl` 類別的 <xref:System.Windows.Forms.UserControl.Load> 事件處理常式中。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## 顯示執行窗格  
 在加入控制項後，執行窗格會成為可見。  
  
#### 若要顯示執行窗格  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**ThisDocument.vb**\] 或 \[**ThisDocument.cs**\]，然後按一下捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  在 `ThisDocument` 類別最上方建立新的控制項執行個體 \(Instance\)，使其看起來如下列範例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  將程式碼加入至 `ThisDocument` 的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式，使其看起來如下列範例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## 測試應用程式  
 現在您可以測試文件，確認當文件開啟時，執行窗格也會顯示。  測試執行窗格控制項的主從式關聯，確認當按一下 \[**插入**\] 按鈕時，資料會填入 Word 資料表。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  確認可以看見執行窗格。  
  
3.  在下拉式方塊中選取公司，並且確認 \[**產品**\] 清單方塊中項目的變更。  
  
4.  選取產品，在執行窗格上按一下 \[**插入**\]，確認產品詳細資料已加入至 Word 中的資料表。  
  
5.  插入不同的公司其他產品。  
  
## 後續步驟  
 這個逐步解說顯示將資料繫結至 Word 中執行窗格上的控制項之基本概念。  以下則是接下來的一些工作：  
  
-   將資料繫結至 Excel 中的控制項。  如需詳細資訊，請參閱[逐步解說：將資料繫結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。  
  
-   部署專案。  如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  