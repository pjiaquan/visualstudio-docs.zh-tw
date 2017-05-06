---
title: "XmlMappedRange 控制項"
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
  - "XMLMappedRange 控制項"
  - "XMLMappedRange 控制項, 資料繫結"
  - "XMLMappedRange 控制項, 事件"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange 控制項
  只有當非重複的結構描述項目對應至 Microsoft Office Excel 的儲存格時，才會建立 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項範圍。  例如，當結構描述項目的 `maxOccurs` 屬性等於 1 時。  在 Visual Studio 建立 XML 對應的範圍之後，您可以直接對其進行程式設計，而不必周遊 Excel 物件模型。  您只有在移除項目對應之後，才可以刪除 Excel 中的 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需觀看相關示範影片，請參閱[如何在 Excel 中使用 XML 對應？](http://go.microsoft.com/fwlink/?LinkID=130288)\(英文\)。  
  
## 將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項支援繫結至單一資料欄位 \(簡單資料繫結\)。  <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項可以支援複雜資料繫結，在重複的結構描述項目對應至儲存格中時，會自動建立該控制項。  如需詳細資訊，請參閱[ListObject 控制項](../vsto/listobject-control.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項使用 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性繫結至資料來源。  將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 加入至工作表儲存格時，Visual Studio 會自動從對應之儲存格的資料產生資料集，並將控制項繫結至該資料集。  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 的預設資料繫結屬性是 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>。  
  
 如果繫結資料集中的資料是透過任何機制進行了更新，<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項則會反映這些變更。  
  
## 格式  
 您可以將相同的格式套用至 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項，其可套用至 <xref:Microsoft.Office.Interop.Excel.Range>。  包括框線、字型、數字格式和樣式。  
  
## 事件  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項可以使用的事件為：  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## 請參閱  
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：將 XMLMappedRange 控制項加入至工作表](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：在 Visual Studio 內將結構描述對應至工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  