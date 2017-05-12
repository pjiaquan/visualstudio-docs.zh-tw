---
title: "如何：以程式設計方式將樣式套用至活頁簿中的範圍"
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
  - "範圍，樣式"
  - "樣式，活頁簿範圍"
  - "活頁簿，樣式"
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 如何：以程式設計方式將樣式套用至活頁簿中的範圍
  您可以將具名樣式套用至活頁簿中的區域。 Excel 提供多個預先定義的樣式。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 \[儲存格格式\] 對話方塊會顯示格式化儲存格可使用的所有選項，而且每個選項都可從程式碼取得。 若要在 Excel 中顯示這個對話方塊，請按一下 \[格式\] 功能表上的 \[儲存格\]。  
  
### 將樣式套用至文件層級自訂中的具名範圍  
  
1.  建立新的樣式，並設定其屬性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#53)]  
  
2.  建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，為其指派文字，然後套用新的樣式。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#54)]  
  
### 從文件層級自訂中的具名範圍清除樣式  
  
1.  將內文樣式套用至範圍。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#55)]  
  
### 將樣式套用到 VSTO 增益集中的具名範圍  
  
1.  建立新的樣式，並設定其屬性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#28)]  
  
2.  建立 <xref:Microsoft.Office.Interop.Excel.Range>，為其指派文字，然後套用新的樣式。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#29)]  
  
### 從 VSTO 增益集中的具名範圍清除樣式  
  
1.  將內文樣式套用至範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#56)]  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  