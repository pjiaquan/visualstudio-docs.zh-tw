---
title: "逐步解說：將資料繫結至 Excel 執行窗格上的控制項"
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
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 逐步解說：將資料繫結至 Excel 執行窗格上的控制項
  本逐步解說示範如何將資料繫結至 Microsoft Office Excel 執行窗格上的控制項。  控制項示範 SQL Server 資料庫中資料表之間的主從式關聯。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   將控制項加入至工作表。  
  
-   建立執行窗格控制項。  
  
-   將資料繫結 Windows Form 控制項加入至執行窗格控制項。  
  
-   在應用程式開啟時顯示執行窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   與具有 Northwind SQL Server 範例資料庫之伺服器的連線。  
  
-   從 SQL Server 資料庫讀取及寫入該資料庫的使用權限。  
  
## 建立專案  
 第一步是建立 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 My Excel Actions Pane 的 Excel 活頁簿專案。  在精靈中選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 **My Excel Actions Pane** 專案加入至 \[**方案總管**\]。  
  
## 在專案中加入新資料來源  
  
#### 若要在專案中加入新資料來源  
  
1.  如果 \[**資料來源**\] 視窗中不可見，請顯示它，請在功能表列上，選擇 \[**檢視**\]\]，則 \[**其他視窗**\]， \[**資料來源**\]。  
  
2.  選取 \[**加入新資料來源**\] 啟動 \[**資料來源組態精靈**\]。  
  
3.  選取 \[**資料庫**\]，再按一下 \[**下一步**\]。  
  
4.  選取與 Northwind 範例 SQL Server 資料庫的資料連接，或使用 \[**新增連接**\] 按鈕加入新的連接。  
  
5.  按一下 \[**下一步**\]。  
  
6.  如果已經選取，請清除儲存連接的選項，然後按一下 \[**下一步**\]。  
  
7.  在 \[**資料庫物件**\] 視窗中，展開 \[**資料表**\] 節點。  
  
8.  選取 \[**供應商**\] 資料表旁的核取方塊。  
  
9. 展開 \[**產品**\] 資料表，並選取 \[**ProductName**\]、\[**SupplierID**\]、\[**QuantityPerUnit**\] 和 \[**UnitPrice**\]。  
  
10. 按一下 \[完成\]。  
  
 精靈會將 \[**供應商**\] 資料表和 \[**產品**\] 資料表加入至 \[**資料來源**\] 視窗，  也會將具型別資料集加入至 \[**方案總管**\] 中可以看得到的專案。  
  
## 將控制項加入至工作表  
 接下來，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項和 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入至第一個工作表。  
  
#### 若要加入 NamedRange 控制項和 ListObject 控制項  
  
1.  驗證 \[**我的 Excel 動作 Pane.xlsx**\] 活頁簿在 Visual Studio 中開啟設計工具，以 `Sheet1` 所顯示的。  
  
2.  在 \[**資料來源**\] 視窗中，展開 \[**供應商**\] 資料表。  
  
3.  按一下 \[**公司名稱**\] 節點上的下拉箭號，然後選取 \[**NamedRange**\]。  
  
4.  將 \[**公司名稱**\] 從 \[**資料來源**\] 視窗拖曳到 `Sheet1` 中的 \[**A2**\] 儲存格。  
  
     在 \[**A2**\] 儲存格中會建立一個名為 `CompanyNameNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，並會顯示文字 \<CompanyName\>。  同時，會將名為 `suppliersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、資料表配接器，以及 <xref:System.Data.DataSet> 加入至專案。  控制項繫結至 <xref:System.Windows.Forms.BindingSource>，繼而又繫結至 <xref:System.Data.DataSet> 執行個體。  
  
5.  在 \[**資料來源**\] 視窗中，向下捲動超過 \[**供應商**\] 資料表底下的資料行。  位在清單底部的是 \[**產品**\] 資料表。由於它是 \[**供應商**\] 資料表的子系，因而位在該處。  請選取這個 \[**產品**\] 資料表，不要選取與 \[**供應商**\] 資料表位於相同層級的資料表，然後按一下顯示的下拉箭號。  
  
6.  在下拉式清單中按一下 \[**ListObject**\]，然後將 \[**產品**\] 資料表拖曳到 `Sheet1` 中的 \[**A6**\] 儲存格。  
  
     \[**A6**\] 儲存格中會建立一個名為 `ProductNameListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  同時，會將名為 `productsBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 和資料表配接器 \(Adapter\) 加入至專案。  控制項繫結至 <xref:System.Windows.Forms.BindingSource>，繼而又繫結至 <xref:System.Data.DataSet> 執行個體。  
  
7.  \(僅適用於 C\#\) 選取元件匣上的 \[**suppliersBindingSource**\]，並在 \[**屬性**\] 視窗中，將 \[**Modifiers**\] 屬性變更為 Internal。  
  
## 將控制項加入至執行窗格  
 接下來，您需要包含下拉式方塊的執行窗格控制項。  
  
#### 若要加入執行窗格控制項  
  
1.  在 \[**方案總管**\] 中選取 **My Excel Actions Pane** 專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
3.  選取 \[**加入新項目**\] 對話方塊中的 \[**執行窗格控制項**\]，將其命名為 **ActionsControl**，然後按一下 \[**加入**\]。  
  
#### 若要將資料繫結 Windows Form 控制項加入至執行窗格控制項  
  
1.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，拖曳 <xref:System.Windows.Forms.ComboBox> 控制項至執行窗格控制項。  
  
2.  將 \[**Size**\] 屬性變更為 171, 21。  
  
3.  調整使用者控制項以符合下拉式方塊的大小。  
  
## 將執行窗格上的控制項繫結至資料  
 在本節中，您會將 <xref:System.Windows.Forms.ComboBox> 的資料來源，設定為與工作表上 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的資料來源相同。  
  
#### 若要設定控制項的資料繫結屬性  
  
1.  以滑鼠右鍵按一下執行窗格控制項，然後按一下 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至執行窗格控制項的 <xref:System.Windows.Forms.UserControl.Load> 事件。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  在 C\# 中，您必須建立 `ActionsControl` 的事件處理常式。  您可以將這個程式碼放在 `ActionsControl` 建構函式 \(Constructor\) 中。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## 顯示執行窗格  
 執行窗格要到您在執行階段加入控制項後，才會顯示。  
  
#### 若要顯示執行窗格  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 ThisWorkbook.vb 或 ThisWorkbook.cs，然後按一下 \[**檢視程式碼**\]。  
  
2.  在 `ThisWorkbook` 類別 \(Class\) 中建立使用者控制項的新執行個體 \(Instance\)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  在 `ThisWorkbook` 的 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件處理常式中，將控制項加入至執行窗格。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## 測試應用程式  
 現在您可以測試文件，確認當文件開啟時，執行窗格也會開啟，而且控制項具有主從式關聯性。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  確認可以看見執行窗格。  
  
3.  在清單方塊中選取一家公司。  確認公司名稱列在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項中，且產品詳細資料列在 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中。  
  
4.  選取不同的公司，確認公司名稱和產品詳細資料會適當地變更。  
  
## 後續步驟  
 以下則是接下來的一些工作：  
  
-   將資料繫結至 Word 中的控制項。  如需詳細資訊，請參閱[逐步解說：在 Word 執行窗格將資料繫結至控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
-   部署專案。  如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：管理執行窗格的控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  