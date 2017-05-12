---
title: "如何：以程式設計方式在活頁簿中加入新的工作表"
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
  - "活頁簿，加入工作表"
  - "活頁簿，建立工作表"
  - "工作表，建立"
  - "工作表，加入活頁簿"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 如何：以程式設計方式在活頁簿中加入新的工作表
  您可以用程式設計方式建立工作表，然後將工作表加入活頁簿的工作表集合。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文件層級自訂的活頁簿中加入新的工作表  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 如果要加入 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目，您應該在設計階段加入工作表。  
  
### 在 VSTO 增益集的活頁簿中加入新的工作表  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 您也可以從原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  