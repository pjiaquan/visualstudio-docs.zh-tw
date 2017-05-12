---
title: "逐步解說：文件層級專案中的複雜資料繫結"
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
  - "複雜資料 [Visual Studio 中的 Office 程式開發]"
  - "資料 [Visual Studio 中的 Office 程式開發], 資料繫結"
  - "資料繫結 [Visual Studio 中的 Office 程式開發], 多個資料行"
  - "多重資料行資料繫結 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 逐步解說：文件層級專案中的複雜資料繫結
  本逐步解說示範使用文件層級專案進行複雜資料繫結的基本概念。  您可以將 Microsoft Office Excel 工作表中的多個儲存格，繫結至 Northwind SQL Server 資料庫中的欄位。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   將資料來源加入至活頁簿專案。  
  
-   將資料繫結控制項加入至工作表。  
  
-   將資料變更儲存回資料庫。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   與具有 Northwind SQL Server 範例資料庫之伺服器的連線。  
  
-   從 SQL Server 資料庫讀取及寫入該資料庫的使用權限。  
  
## 建立新專案  
 第一步是建立 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 **My Complex Data Binding** 的 Excel 活頁簿專案。  在精靈中選取 \[**建立新文件**\]。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 My Complex Data Binding 專案加入至 \[**方案總管**\]。  
  
## 建立資料來源  
 請使用 \[**資料來源**\] 視窗，將具型別資料集加入您的專案。  
  
#### 建立資料來源  
  
1.  如果 \[**資料來源**\] 視窗中不可見，請顯示它，請在功能表列上，選擇 \[**檢視**\]\]，則 \[**其他視窗**\]， \[**資料來源**\]。  
  
2.  選取 \[**加入新資料來源**\] 啟動 \[**資料來源組態精靈**\]。  
  
3.  選取 \[**資料庫**\]，再按一下 \[**下一步**\]。  
  
4.  選取與 Northwind 範例 SQL Server 資料庫的資料連接，或使用 \[**新增連接**\] 按鈕加入新的連接。  
  
5.  在選取或建立連接後，請按 \[**下一步**\]。  
  
6.  如果已經選取，請清除儲存連接的選項，然後按一下 \[**下一步**\]。  
  
7.  在 \[**資料庫物件**\] 視窗中，展開 \[**資料表**\] 節點。  
  
8.  選取 \[**Employees**\] 資料表旁的核取方塊。  
  
9. 按一下 \[完成\]。  
  
 精靈會將 \[**Employees**\] 資料表加入至 \[**資料來源**\] 視窗，  也會將具型別資料集加入至 \[**方案總管**\] 中可以看得到的專案。  
  
## 將控制項加入至工作表  
 工作表將在活頁簿開啟時顯示 \[**Employees**\] 資料表。  使用者將能對資料進行變更，然後按一下按鈕，將變更儲存回資料庫。  
  
 若要自動繫結工作表與資料表，您可以從 \[**資料來源**\] 視窗將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入至工作表。  若要讓使用者能夠選擇儲存變更，請從 \[**工具箱**\] 加入 <xref:System.Windows.Forms.Button> 控制項。  
  
#### 加入清單物件  
  
1.  驗證 \[**我的複雜資料 Binding.xlsx**\] 活頁簿在 Visual Studio 中開啟設計工具，並顯示 \[**Sheet1**\] 。  
  
2.  開啟 \[**資料來源**\] 視窗，然後選取 \[**Employees**\] 節點。  
  
3.  按一下顯示的下拉箭號。  
  
4.  選取下拉式清單中的 \[**ListObject**\]。  
  
5.  將 \[**Employees**\] 資料表拖曳至 \[**A6**\] 儲存格。  
  
     \[**A6**\] 儲存格中會建立一個名為 `EmployeesListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  同時，會將名為 `EmployeesBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、資料表配接器，以及 <xref:System.Data.DataSet> 執行個體加入至專案。  控制項繫結至 <xref:System.Windows.Forms.BindingSource>，繼而又繫結至 <xref:System.Data.DataSet> 執行個體。  
  
#### 若要加入按鈕  
  
1.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入至工作表的 \[**A4**\] 儲存格。  
  
 下一個步驟是在工作表開啟時將文字加入至按鈕。  
  
## 初始化控制項  
 將文字加入至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中的按鈕。  
  
#### 若要初始化控制項  
  
1.  在 \[**方案總管**\] 中，在 \[**Sheet1.vb**\] 或 \[**Sheet1.cs**\] 上按一下滑鼠右鍵，再按捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至 `Sheet1_Startup` 方法，以設定 b`utton` 的文字。  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  如果是 C\#，請加入 <xref:System.Windows.Forms.Control.Click> 事件的事件處理常式至 `Sheet1_Startup` 方法。  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 現在，請加入程式碼，以處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
## 將變更儲存至資料庫  
 將對資料所做的任何變更明確存回資料庫之前，這些變更都只存在本機資料集中。  
  
#### 若要將變更儲存至資料庫  
  
1.  為 b`utton` 的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，認可對資料集所做的所有變更儲存到資料庫中。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## 測試應用程式  
 現在您可以測試活頁簿，確認資料將如預期般顯示，而且您可以在清單物件中操作該資料。  
  
#### 若要測試資料繫結  
  
-   按 F5。  
  
     確認當活頁簿開啟時，清單物件中會填入來自 \[**Employees**\] 資料表的資料。  
  
#### 若要修改資料  
  
1.  按一下 \[**B7**\] 儲存格，此儲存格應該包含 \[**Davolio**\] 的名稱。  
  
2.  輸入 Anderson 的名稱，然後按 ENTER。  
  
#### 若要修改資料行行首  
  
1.  按一下包含資料行行首 \[**LastName**\] 的儲存格。  
  
2.  輸入 Last Name，在兩個字中間包含一個空格，然後按 ENTER。  
  
#### 若要儲存資料  
  
1.  在工作表上按一下 \[**儲存**\]。  
  
2.  結束 Excel。  當系統提示您儲存所做的變更時，請按一下 \[**否**\]。  
  
3.  按 F5，再次執行專案。  
  
     清單物件中便會填入來自 \[**Employees**\] 資料表的資料。  
  
4.  請注意，\[**B7**\] 儲存格中的名稱仍為 Anderson，也就是您所進行並儲存到資料庫的資料變更。  資料行行首 \[**LastName**\] 則已變更回沒有空格的原始格式，因為資料行行首並未繫結至資料庫，而且您也沒有儲存對工作表所做的變更。  
  
#### 若要加入新資料列  
  
1.  在清單物件內選取儲存格。  
  
     新資料列會出現在清單底部，而且新資料列的第一個儲存格中會出現星號 \(**\***\)。  
  
2.  在空白資料列中加入下列資訊。  
  
    |EmployeeID|LastName|FirstName|標題|  
    |----------------|--------------|---------------|--------|  
    |10|Ito|Shu|Sales Manager|  
  
#### 若要刪除資料列  
  
-   以滑鼠右鍵按一下工作表最左邊的數字 \[16\] \(第 16 列\)，然後按一下 \[**刪除**\]。  
  
#### 若要對清單中的資料列進行排序  
  
1.  在清單內選取儲存格。  
  
     每個資料行行首中都會顯示箭號按鈕。  
  
2.  按一下 \[**Last Name**\] 資料行行首中的箭號按鈕。  
  
3.  按一下 \[**遞增排序**\]。  
  
     會按照姓氏的字母順序排列資料列。  
  
#### 若要篩選資訊  
  
1.  在清單內選取儲存格。  
  
2.  按一下 \[**Title**\] 資料行行首中的箭號按鈕。  
  
3.  按一下 \[**Sales Representative**\]。  
  
     清單中只會顯示 \[**Title**\] 資料行中具有 \[**Sales Representative**\] 的資料列。  
  
4.  再按一下 \[**Title**\] 資料行行首中的箭號按鈕。  
  
5.  按一下 \[**\(全部\)**\]。  
  
     會移除篩選並顯示所有資料列。  
  
## 後續步驟  
 這個逐步解說示範將資料庫中資料表繫結至清單物件的基本步驟。  以下則是接下來的一些工作：  
  
-   快取資料，使您能夠離線使用資料。  如需詳細資訊，請參閱[如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   部署方案。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   建立欄位和資料表之間的主從式 \(Master\/Detail\) 關聯。  如需詳細資訊，請參閱[逐步解說：使用快取資料集來建立主從式關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 方案的資料](../vsto/data-in-office-solutions.md)   
 [逐步解說：文件層級專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  