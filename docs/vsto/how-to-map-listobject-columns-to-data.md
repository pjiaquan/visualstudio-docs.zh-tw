---
title: "如何：將 ListObject 欄對應到資料"
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
  - "資料 [Visual Studio 中的 Office 程式開發]，對應至 ListObject 資料行"
  - "ListObject 控制項，對應資料"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：將 ListObject 欄對應到資料
  當您將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項繫結到 <xref:System.Data.DataTable> 時，您可能不想在清單中顯示所有資料行，或可能有某些資料行未繫結至資料。 當您呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法時，您可以對應想要顯示在 <xref:Microsoft.Office.Tools.Excel.ListObject> 的資料行。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![視訊的連結](~/data-tools/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱[如何：在 Excel 中建立連接至 SharePoint 清單的清單](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
## 對應資料行  
  
#### 對應資料表和清單中的資料行  
  
1.  在類別層級建立 <xref:System.Data.DataTable>。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  將範例資料行和資料加入 `Sheet1` 類別的 `Startup` 事件處理常式 \(文件層級專案\) 或 `ThisAddIn` 類別 \(VSTO 增益集專案\)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 清單物件會繫結至新建立的 <xref:System.Data.DataTable>，但清單物件中的資料行順序會和 <xref:System.Data.DataTable> 顯示的順序不同。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## 指定未對應的資料行  
 當您將資料行對應至 <xref:System.Data.DataTable> 時，您也可以透過傳入空字串，指定某些資料行不應該繫結至資料。 不繫結至資料的新資料行，就會加入 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  
  
#### 對應 ListObject 資料行時指定未對應的資料行  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 使用空字串表示該處加入了未對應的資料行，本例為介於標題資料行和姓氏資料行之間。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## 編譯程式碼  
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 `list1` 的 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：將資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控制項](../vsto/listobject-control.md)  
  
  