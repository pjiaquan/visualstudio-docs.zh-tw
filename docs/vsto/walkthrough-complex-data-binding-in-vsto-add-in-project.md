---
title: "逐步解說：VSTO 增益集專案中的複雜資料繫結 | Microsoft Docs"
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
  - "資料繫結 [Visual Studio 中的 Office 程式開發]，Excel"
  - "資料 [Visual Studio 中的 Office 程式開發]，繫結資料"
  - "複雜資料 [Visual Studio 中的 Office 程式開發]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：VSTO 增益集專案中的複雜資料繫結
  您可以將資料繫結至 VSTO 增益集專案中的主控制項和 Windows Form 控制項。 本逐步解說示範如何在執行階段將控制項加入 Microsoft Office Excel 工作表，以及將控制項繫結至資料。  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在執行階段將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入工作表。  
  
-   建立可將控制項連接到資料集執行個體的 <xref:System.Windows.Forms.BindingSource>。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   已附加 `AdventureWorksLT` 範例資料庫之執行中 SQL Server 2005 或 SQL Server 2005 Express 執行個體的存取權。 您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?LinkId=115611)下載 `AdventureWorksLT` 資料庫。 如需附加資料庫的詳細資訊，請參閱下列主題：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱[如何：附加資料庫 \(SQL Server Management Studio\)](http://msdn.microsoft.com/zh-tw/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令列附加資料庫，請參閱[如何：將資料庫檔案附加到 SQL Server Express](http://msdn.microsoft.com/zh-tw/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## 建立新專案  
 第一步是建立 Excel VSTO 增益集專案。  
  
#### 若要建立新的專案  
  
1.  使用 Visual Basic 或 C\#，建立名稱為「從資料庫填入工作表」的 Excel VSTO 增益集專案。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會開啟 `ThisAddIn.vb` 或 `ThisAddIn.cs` 檔案，然後將 \[從資料庫填入工作表\] 專案加入方案總管。  
  
## 建立資料來源  
 使用 \[資料來源\] 視窗將型別資料集加入專案。  
  
#### 將具類型資料集加入專案  
  
1.  如果看不到 \[**資料來源**\] 視窗，請在功能表列選擇 \[**檢視**\]、\[**其他視窗**\]、\[**資料來源**\] 即可顯示。  
  
2.  選擇 \[**加入新資料來源**\] 以啟動 \[**資料來源組態精靈**\]。  
  
3.  按一下 \[資料庫\]，然後按 \[下一步\]。  
  
4.  如果您有 `AdventureWorksLT` 資料庫的現有連接，請選擇這個連接，然後按 \[下一步\]。  
  
     否則，請按一下 \[新增連接\]，然後使用 \[加入連接\] 對話方塊建立新的連接。 如需詳細資訊，請參閱[如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
5.  在 \[將連接字串儲存到應用程式組態檔\] 頁面上，按 \[下一步\]。  
  
6.  在 \[選擇您的資料庫物件\] 頁面中，展開 \[資料表\]，然後選取 \[Address \(SalesLT\)\]。  
  
7.  按一下 \[**完成**\]。  
  
     AdventureWorksLTDataSet.xsd 檔案會加入方案總管中。 這個檔案會定義下列項目：  
  
    -   名為 `AdventureWorksLTDataSet` 的具類型資料集。 這個資料集代表 AdventureWorksLT 資料庫中 \[Address \(SalesLT\)\] 資料表的內容。  
  
    -   名為 TableAdapter 的 `AddressTableAdapter`。 這個 TableAdapter 可以用來讀取和寫入 `AdventureWorksLTDataSet` 中的資料。 如需詳細資訊，請參閱[TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
     您將在本逐步解說稍後用到這兩個物件。  
  
## 建立控制項並將控制項繫結至資料  
 在本逐步解說中，只要使用者開啟活頁簿，<xref:Microsoft.Office.Tools.Excel.ListObject> 控制項便會顯示您選取的資料表中的所有資料。 清單物件使用 <xref:System.Windows.Forms.BindingSource> 將控制項連接到資料庫。  
  
 如需將控制項繫結至資料的詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### 加入清單物件、資料集和資料表配接器  
  
1.  在 `ThisAddIn` 類別中，宣告下列控制項來顯示 `AdventureWorksLTDataSet` 資料集的 `Address` 資料表。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  在 `ThisAddIn_Startup` 方法中，加入下列程式碼來初始化資料集，並在資料集中填入來自 `AdventureWorksLTDataSet` 資料集的資訊。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  將下列程式碼加入至 `ThisAddIn_Startup` 方法。 這會產生可擴充工作表的主項目。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  建立一個範圍並加入 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  使用 <xref:System.Windows.Forms.BindingSource> 將清單物件繫結至 `AdventureWorksLTDataSet`。 將您要繫結的資料行名稱傳入清單物件。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## 測試增益集  
 當您開啟 Excel 時，<xref:Microsoft.Office.Tools.Excel.ListObject> 控制項會顯示 `AdventureWorksLTDataSet` 資料集之 `Address` 資料表中的資料。  
  
#### 測試 VSTO 增益集  
  
-   請按 **F5**。  
  
     工作表中會建立名為 `addressListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 同時也會將名為 `adventureWorksLTDataSet` 的資料集物件和名為 `addressBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 加入專案。<xref:Microsoft.Office.Tools.Excel.ListObject> 會繫結至 <xref:System.Windows.Forms.BindingSource>，而後者則繫結至資料集物件。  
  
## 請參閱  
 [Office 方案的資料](../vsto/data-in-office-solutions.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：將資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：將服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：在工作表中捲動資料庫記錄](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [逐步解說：文件層級專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [逐步解說：文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [使用在 Office 方案概觀中的本機資料庫檔案](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [使用在 Office 方案概觀中的本機資料庫檔案](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [連接至 Windows Form 應用程式中的資料](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)  
  
  