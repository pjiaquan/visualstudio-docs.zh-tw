---
title: "如何：以程式設計方式加入及刪除工作表註解 | Microsoft Docs"
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
  - "範圍，註解"
  - "工作表，註解"
  - "註解，工作表"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：以程式設計方式加入及刪除工作表註解
  您可以透過程式設計方式，加入及刪除 Microsoft Office Excel 工作表中的註解。 註解只能加入單一儲存格，而不能加入多個儲存格範圍。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 在文件層級專案中加入及刪除註解  
 下列範例假設名為 `Sheet1` 的工作表上有名為 `dateComment` 的單一儲存格 <xref:Microsoft.Office.Tools.Excel.NamedRange>。  
  
#### 將新註解加入具名範圍  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> 方法，並提供註解文字。 這段程式碼必須放在 `Sheet1` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### 從具名範圍中刪除註解  
  
1.  確認範圍中有註解，再加以刪除。 這段程式碼必須放在 `Sheet1` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## 在 VSTO 增益集專案中加入及刪除註解  
 下列範例假設使用中工作表上有名為 `dateComment` 的單一儲存格 <xref:Microsoft.Office.Interop.Excel.Range>。  
  
#### 將新註解加入 Excel 範圍  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Excel.Range> 的 <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> 方法，並提供註解文字。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### 從 Excel 範圍中刪除註解  
  
1.  確認範圍中有註解，再加以刪除。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式顯示工作表註解](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)  
  
  