---
title: "逐步解說：VSTO 增益集專案中的簡單資料繫結 | Microsoft Docs"
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
  - "資料 [Visual Studio 中的 Office 程式開發]，繫結資料"
  - "資料繫結 [Visual Studio 中的 Office 程式開發]，Word"
  - "資料 [Visual Studio 中的 Office 程式開發]，簡單繫結資料"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 逐步解說：VSTO 增益集專案中的簡單資料繫結
  您可以將資料繫結至 VSTO 增益集專案中的主控制項和 Windows Forms 控制項。 本逐步解說示範如何將控制項加入 Microsoft Office Word 文件，以及在執行階段將控制項繫結至資料。  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段將 <xref:Microsoft.Office.Tools.Word.ContentControl> 加入文件。  
  
-   建立將控制項連接至資料集的 <xref:System.Windows.Forms.BindingSource> 執行個體。  
  
-   讓使用者能夠捲動記錄及在控制項中檢視它們。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   已附加 `AdventureWorksLT` 範例資料庫之執行中 SQL Server 2005 或 SQL Server 2005 Express 執行個體的存取權。 您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?LinkId=115611)下載 `AdventureWorksLT` 資料庫。 如需附加資料庫的詳細資訊，請參閱下列主題：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱[如何：附加資料庫 \(SQL Server Management Studio\)](http://msdn.microsoft.com/zh-tw/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令列附加資料庫，請參閱[如何：將資料庫檔案附加到 SQL Server Express](http://msdn.microsoft.com/zh-tw/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## 建立新專案  
 第一步是建立 Word VSTO 增益集專案。  
  
#### 若要建立新的專案  
  
1.  使用 Visual Basic 或 C\#，建立名稱為 \[**從資料庫填入文件**\] 的 Word VSTO 增益集專案。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會開啟 ThisAddIn.vb 或 ThisAddIn.cs 檔案，並將 \[**從資料庫填入文件**\] 專案加入**方案總管**。  
  
2.  如果您的專案以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 為目標，請加入 Microsoft.Office.Tools.Word.v4.0.Utilities.dll 組件的參考。 本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Forms 控制項加入文件。  
  
## 建立資料來源  
 使用 \[**資料來源**\] 視窗將型別資料集加入專案。  
  
#### 將具類型資料集加入專案  
  
1.  如果看不到 \[**資料來源**\] 視窗，請在功能表列選擇 \[**檢視**\]、\[**其他視窗**\]、\[**資料來源**\] 即可顯示。  
  
2.  選擇 \[**加入新資料來源**\] 以啟動 \[**資料來源組態精靈**\]。  
  
3.  按一下 \[**資料庫**\]，然後按 \[**下一步**\]。  
  
4.  如果您有 `AdventureWorksLT` 資料庫的現有連接，請選擇這個連接，然後按 \[**下一步**\]。  
  
     否則，請按一下 \[**新增連接**\]，然後使用 \[**加入連接**\] 對話方塊建立新的連接。 如需詳細資訊，請參閱[如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
5.  在 \[**將連接字串儲存到應用程式組態檔**\] 頁面上，按 \[**下一步**\]。  
  
6.  在 \[**選擇您的資料庫物件**\] 頁面中，展開 \[**資料表**\]，然後選取 \[**Customer \(SalesLT\)**\]。  
  
7.  按一下 \[**完成**\]。  
  
     AdventureWorksLTDataSet.xsd 檔案已加入**方案總管**中。 這個檔案會定義下列項目：  
  
    -   具類型資料集，名稱為 `AdventureWorksLTDataSet`。 此資料集代表 AdventureWorksLT 資料庫中 **Customer \(SalesLT\)** 資料表的內容。  
  
    -   名為 TableAdapter 的 `CustomerTableAdapter`。 這個 TableAdapter 可以用來讀取和寫入 `AdventureWorksLTDataSet` 中的資料。 如需詳細資訊，請參閱[TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
     您將在本逐步解說稍後用到這兩個物件。  
  
## 建立控制項並將控制項繫結至資料  
 在本逐步解說中，檢視資料庫記錄的介面非常基本，而且它就建立在文件內。 一個 <xref:Microsoft.Office.Tools.Word.ContentControl> 一次顯示單一資料庫記錄，而兩個 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項可讓您來回捲動記錄。 內容控制項使用 <xref:System.Windows.Forms.BindingSource> 連接到資料庫。  
  
 如需將控制項繫結至資料的詳細資訊，請參閱 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### 在文件中建立介面  
  
1.  在 `ThisAddIn` 類別中，宣告下列控制項來顯示和捲動 `AdventureWorksLTDataSet` 資料庫的 `Customer` 資料表。  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  在 `ThisAddIn_Startup` 方法中，加入下列程式碼來初始化資料集、在資料集填入來自 `AdventureWorksLTDataSet` 資料庫的資訊。  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  將下列程式碼加入至 `ThisAddIn_Startup` 方法。 這會產生可擴充文件的主項目。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  在文件開頭定義數個範圍。 這些範圍會識別插入文字和放置控制項的位置。  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  將介面控制項加入先前定義的範圍。  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  使用 <xref:System.Windows.Forms.BindingSource> 將內容控制項繫結至 `AdventureWorksLTDataSet`。 C\# 開發人員請加入 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項的兩個事件處理常式。  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  加入下列程式碼來瀏覽資料庫記錄。  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## 測試增益集  
 當您開啟 Word 時，內容控制項會顯示來自 `AdventureWorksLTDataSet` 資料集的資料。 按 \[**下一個**\] 和 \[**前一個**\] 按鈕，即可捲動資料庫記錄。  
  
#### 測試 VSTO 增益集  
  
1.  請按 **F5**。  
  
     會建立名為 `customerContentControl` 的內容控制項並填入資料。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 `customerBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 會加入專案。<xref:Microsoft.Office.Tools.Word.ContentControl> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。  
  
2.  按 \[**下一個**\] 和 \[**前一個**\] 按鈕，即可捲動資料庫記錄。  
  
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
 [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [使用在 Office 方案概觀中的本機資料庫檔案](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [連接至 Windows Form 應用程式中的資料](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)  
  
  