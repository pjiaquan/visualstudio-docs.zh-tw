---
title: "將資料繫結至 Office 方案中的控制項"
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
  - "Office 文件 [Visual Studio 中的 Office 程式開發]、連接到資料"
  - "資料，資料繫結"
  - "資料繫結"
  - "資料繫結，Office 方案"
  - "資料繫結，控制項"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，資料繫結"
  - "控制項，資料繫結"
ms.assetid: b6faaed7-df9b-4d78-9863-e515cd5c7ed9
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 將資料繫結至 Office 方案中的控制項
  您可以將 Microsoft Office Word 文件或 Microsoft Office Excel 工作表中的 Windows Form 控制項和「主控制項」\(host control\) 繫結至資料來源，讓控制項自動顯示資料。 您可以將資料繫結至應用程式層級和文件層級專案中的控制項。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 主控制項會擴充 Word 和 Excel 物件模型中的物件，例如 Word 中的內容控制項和 Excel 中的具名範圍。 如需詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 Windows Form 和主控制項都會使用 Windows Form 資料繫結模型，這個模型同時支援對資料集和資料表等資料來源執行「簡單資料繫結」\(simple data binding\) 和「複雜資料繫結」\(complex data binding\)。 如需 Windows Form 中資料繫結模型的完整資訊，請參閱[資料繫結和 Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)。  
  
 ![視訊的連結](~/data-tools/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱[如何：使用 Excel 中的資料庫資料](http://go.microsoft.com/fwlink/?LinkID=130287)。  
  
## 簡單資料繫結  
 當控制項屬性繫結至單一資料項目時，例如資料表中的值，便存在簡單資料繫結。 例如，<xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項具有 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性，該屬性可繫結至資料集中的欄位。 當資料集中的欄位變更時，具名範圍中的值也會變更。 除了 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項以外，所有主控制項都支援簡單資料繫結。<xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項是一個集合，因此不支援資料繫結。  
  
 若要對主控制項執行簡單資料繫結，請將 <xref:System.Windows.Forms.Binding> 加入該控制項的 DataBindings 屬性。<xref:System.Windows.Forms.Binding> 物件代表控制項屬性值與資料項目值之間的簡單繫結。  
  
 下列範例示範如何在文件層級專案中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性繫結至資料項目。  
  
 [!code-csharp[Trin_BindableComponent#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_BindableComponent/CS/Sheet1.cs#4)]
 [!code-vb[Trin_BindableComponent#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_BindableComponent/VB/Sheet1.vb#4)]  
  
 如需示範簡單資料繫結的逐步解說，請參閱[逐步解說：文件層級專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) \(文件層級專案\) 和[逐步解說：VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) \(VSTO 增益集專案\)。  
  
## 複雜資料繫結  
 當控制項屬性繫結至多個資料項目時，例如資料表中的多個資料行，便存在複雜資料繫結。 Excel 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項是唯一支援複雜資料繫結的主控制項。 另外還有許多支援複雜資料繫結的 Windows Form 控制項，例如 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
 若要執行複雜資料繫結，請將控制項的 DataSource 屬性設定為複雜資料繫結所支援的資料來源物件。 例如，<xref:Microsoft.Office.Tools.Excel.ListObject> 控制項的 <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> 屬性可以繫結至資料表中的多個資料行。 資料表中的所有資料會顯示在 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中，而且當資料表中的資料變更時，<xref:Microsoft.Office.Tools.Excel.ListObject> 也會變更。 如需可用於複雜資料繫結的資料來源清單，請參閱 [Windows Form 支援的資料來源](http://msdn.microsoft.com/library/3d2c43f6-462b-4d35-9c86-13e9afe012e1)。  
  
 下列程式碼範例會建立具有兩個 <xref:System.Data.DataTable> 物件的 <xref:System.Data.DataSet>，並將資料填入其中一個資料表。 然後程式碼會將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至含有資料的資料表。 這是示範 Excel 文件層級專案的範例。  
  
 [!code-csharp[Trin_ExcelListObject#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelListObject/CS/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelListObject/VB/Sheet1.vb#18)]  
  
 如需示範複雜資料繫結的逐步解說，請參閱[逐步解說：文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) \(文件層級專案\) 和[逐步解說：VSTO 增益集專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) \(VSTO 增益集專案\)。  
  
## 在文件和活頁簿中顯示資料  
 在文件層級專案中，您可以輕鬆地使用 \[資料來源\] 視窗將資料繫結控制項加入文件或活頁簿，與用於 Windows Form 的方法相同。 如需使用 \[資料來源\] 視窗的詳細資訊，請參閱[將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)和[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。  
  
### 從資料來源視窗拖曳控制項  
 當您從 \[資料來源\] 視窗將某個物件拖曳到文件時，文件上會建立控制項。 所建立的控制項類型取決於您繫結的是單一資料行，還是多個資料行。  
  
 就 Excel 而言，工作表上會針對每個欄位建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，並針對每個包含多個資料列和資料行的資料範圍建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。 您可以在 \[資料來源\] 視窗中選取資料表或欄位，然後從下拉式清單中選擇不同的控制項，來變更這個預設值。  
  
 <xref:Microsoft.Office.Tools.Word.ContentControl> 控制項已加入文件。 內容控制項的類型取決於您選取的欄位資料類型。  
  
### 在文件層級專案的設計階段繫結資料  
 下列主題示範如何在設計階段繫結資料：  
  
-   [如何：將資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [如何：將服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [如何：在工作表中捲動資料庫記錄](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### 在 VSTO 增益集專案中繫結資料  
 在 VSTO 增益集專案中，您只能在執行階段加入控制項。 下列主題示範如何在執行階段繫結資料：  
  
-   [逐步解說：VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [逐步解說：VSTO 增益集專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## 更新繫結至主控制項的資料  
 資料來源與主控制項之間的資料繫結涉及雙向資料更新。 在簡單資料繫結中，資料來源中的變更會自動反映在主控制項中，但主控制項中的變更需要明確的呼叫才能更新資料來源。 這是因為在某些情況下，一個資料繫結欄位中的變更，必須也發生在另一個資料繫結欄位中，才會予以接受。 例如，您可能有兩個欄位，一個用於年齡，另一個用於工作經驗。 工作經驗不可超過年齡。 使用者不可將年齡從 50 更新為 25，然後再將工作經驗從 30 更新為 10，除非該使用者同時進行變更。 為了解決這個問題，簡單資料繫結的欄位會在程式碼明確傳送更新之後才進行更新。  
  
 若要從啟用簡單資料繫結的主控制項更新資料來源，您必須將更新傳送至記憶體內部資料來源 \(例如 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>\)，並傳送至後端資料庫 \(如果方案有使用的話\)。  
  
 使用 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項執行複雜資料繫結時，不需要明確更新記憶體內部資料來源。 在該情況下，變更會自動傳送至記憶體內部資料來源，而不需要其他程式碼。  
  
 如需詳細資訊，請參閱[如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## 請參閱  
 [如何：使用 Excel 中的資料庫資料](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [資料繫結和 Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)   
 [如何：在 Windows Form 上建立簡單繫結控制項](http://msdn.microsoft.com/library/3bcaded8-0f1a-4cc0-8830-f59be253bf4e)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [儲存資料集中的資料](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [如何：使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)   
 [快取資料](../vsto/caching-data.md)   
 [Office 方案的資料](../vsto/data-in-office-solutions.md)  
  
  