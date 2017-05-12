---
title: "如何：以程式設計方式在程式碼中參考工作表範圍"
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
  - "Excel [Visual Studio 中的 Office 程式開發], 參考工作表範圍"
  - "範圍, 參考"
  - "參考工作表範圍"
  - "工作表, 參考範圍"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以程式設計方式在程式碼中參考工作表範圍
  請使用類似的程序來參考 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件的內容。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控制項  
 下列範例會將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 加入至工作表，然後將文字加入至範圍中的儲存格。  
  
#### 若要參考 NamedRange 控制項  
  
1.  指派字串給 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性。  這段程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## 使用原生 Excel 範圍  
 下列範例會將原生 Excel 範圍加入至工作表，然後將文字加入至範圍中的儲存格。  
  
#### 若要參考原生範圍物件  
  
1.  指派字串給範圍的 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 屬性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何：以程式設計方式在工作表中檢查拼字](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以程式設計方式用遞增 &#40;減&#41; 變化的資料自動填滿範圍](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何：以程式設計方式在工作表範圍中搜尋文字](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  