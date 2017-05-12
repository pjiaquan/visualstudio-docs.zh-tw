---
title: "如何：以程式設計方式列印工作表"
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
  - "預覽列印, 工作表"
  - "列印 [Visual Studio 中的 Office 程式開發], 工作表"
  - "工作表, 列印"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式列印工作表
  您可以列印活頁簿中的任何工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 列印文件層級自訂的工作表  
  
#### 列印工作表  
  
1.  呼叫 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> 方法，要求兩個複本，以及在列印前先預覽文件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法可讓您在 \[預覽列印\] 視窗中顯示指定的物件。  下列程式碼假設您有名為 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。  
  
#### 在列印前先預覽頁面  
  
1.  呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## 列印 VSTO 增益集的工作表  
  
#### 列印工作表  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> 方法，要求兩個複本，以及在列印前先預覽文件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法可讓您在 \[預覽列印\] 視窗中顯示指定的物件。  
  
#### 在列印前先預覽頁面  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式在工作表中檢查拼字](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Worksheet 主項目](../vsto/worksheet-host-item.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  