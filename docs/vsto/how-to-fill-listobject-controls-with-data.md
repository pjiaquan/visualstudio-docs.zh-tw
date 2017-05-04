---
title: "如何：將資料填入 ListObject 控制項 | Microsoft Docs"
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
  - "中斷與資料來源的連接"
  - "ListObject 控制項，中斷與資料來源的連線"
  - "ListObject 控制項，填入資料"
  - "資料 [Visual Studio 中的 Office 程式開發]，加入工作表"
  - "資料繫結，ListObject 控制項"
  - "工作表，填入資料"
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：將資料填入 ListObject 控制項
  使用資料繫結也可以快速在文件中加入資料。 將資料繫結至清單物件之後，您可以中斷清單物件的連線，讓它顯示資料但不再繫結至資料來源。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關的影片示範，請參閱[如何：在 Excel 中建立連接至 SharePoint 清單的清單](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
### 將資料繫結至 ListObject 控制項  
  
1.  在類別層級建立 <xref:System.Data.DataTable>。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#20)]  
  
2.  將範例資料行和資料加入 `Sheet1` 類別的 `Startup` 事件處理常式 \(文件層級專案\) 或 `ThisAddIn` 類別 \(應用程式層級專案\)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#21)]  
  
3.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 清單物件中的資料行順序可能不同於 <xref:System.Data.DataTable> 中的出現順序 。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#22)]  
  
### 中斷 ListObject 控制項與資料來源的連線  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 的 `List1` 方法。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#23)]  
  
## 編譯程式碼  
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 `list1` 的 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：將資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何：將服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  