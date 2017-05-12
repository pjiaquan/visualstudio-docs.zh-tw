---
title: "如何：以程式設計方式列出活頁簿中的所有工作表"
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
  - "活頁簿, 列出工作表"
  - "工作表, 列出"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式列出活頁簿中的所有工作表
  <xref:Microsoft.Office.Interop.Excel.Workbook> 類別會提供 <xref:Microsoft.Office.Interop.Excel.Worksheets> 物件。  這個物件在活頁簿中含有所有 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件的集合。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 若要在文件層級自訂中列出活頁簿的全部現有工作表  
  
1.  在 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合中逐一查看每個工作表的名稱，並將名稱傳送到從 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項位移 \(Offset\) 的儲存格。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### 若要在 VSTO 增益集中列出活頁簿的全部現有工作表  
  
1.  在 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合中逐一查看每個工作表的名稱，並將名稱傳送到與 <xref:Microsoft.Office.Interop.Excel.Range> 物件相距某位移的儲存格。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何：以程式設計方式在活頁簿內移動工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  