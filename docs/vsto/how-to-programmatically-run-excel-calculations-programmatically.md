---
title: "如何：以程式設計的方式來執行 Excel 計算功能"
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
  - "計算, 在 Excel 中執行"
  - "Excel [Visual Studio 中的 Office 程式開發], 以程式方式執行計算"
  - "範圍, 執行計算"
  - "活頁簿, 執行計算"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以程式設計的方式來執行 Excel 計算功能
  您要使用類似的程序，執行 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件中的計算功能。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 在 NamedRange 控制項中執行計算  
 下列範例會在儲存格 A1 中建立 <xref:Microsoft.Office.Tools.Excel.NamedRange>，然後計算這個儲存格。  這段程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
#### 若要在 NamedRange 控制項中執行計算  
  
1.  建立已命名的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  呼叫指定之範圍的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## 在原生 Excel 範圍中執行計算  
  
#### 若要在原生 Excel 範圍中執行計算  
  
1.  建立已命名的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  呼叫指定之範圍的 <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  