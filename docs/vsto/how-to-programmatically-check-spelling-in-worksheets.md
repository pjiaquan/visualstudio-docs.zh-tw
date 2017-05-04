---
title: "如何：以程式設計方式在工作表中檢查拼字 | Microsoft Docs"
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
  - "拼字檢查"
  - "拼字檢查程式，工作表"
  - "工作表，檢查拼字"
  - "拼字，在工作表中檢查"
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：以程式設計方式在工作表中檢查拼字
  您可以用程式設計方式檢查工作表中的拼字。 如果工作表中有任何拼寫不正確的字，\[拼字檢查\] 對話方塊就會自動出現。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文件層級自訂中檢查工作表的拼字  
  
1.  呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#45)]  
  
### 在 VSTO 增益集的工作表中檢查拼字  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#22)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計的方式來執行 Excel 計算功能](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  