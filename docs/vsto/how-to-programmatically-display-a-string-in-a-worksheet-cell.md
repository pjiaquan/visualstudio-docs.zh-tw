---
title: "如何：以程式設計方式在工作表儲存格中顯示字串"
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
  - "文字 [Visual Studio 中的 Office 程式開發], 加入至工作表"
  - "工作表, 在儲存格中顯示文字"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 如何：以程式設計方式在工作表儲存格中顯示字串
  這個範例示範如何以程式設計的方式在儲存格中顯示文字。  若要在儲存格中顯示文字，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控制項  
 這個範例會使用名為 `message` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  這個控制項必須是在設計階段加入至文件層級自訂。  下列程式碼必須放在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
#### 若要在 NamedRange 控制項中顯示文字  
  
1.  將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的值設為 **Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## 使用原生 Excel 範圍  
 下列程式碼會以程式設計方式建立新範圍，然後為其分派值。  
  
#### 若要在 Excel 範圍物件中顯示文字  
  
1.  在 `Sheet1` 的儲存格 \[**A1**\] 上擷取範圍，然後將值設為 **Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## 請參閱  
 [逐步解說：使用 Windows Form 收集資料](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office 方案疑難排解](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  