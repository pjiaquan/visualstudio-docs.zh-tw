---
title: "如何：以程式設計方式在工作表中排序資料"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 在工作表中排序"
  - "資料排序, 工作表"
  - "排序資料, 在工作表中"
  - "工作表, 排序資料"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 如何：以程式設計方式在工作表中排序資料
  您可以在執行階段排序工作表範圍和清單中包含的資料。  下列程式碼會先按第一個資料行的資料，再按第二個資料行的資料，排序名為 `Fruits` 的多欄範圍。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 排序文件層級自訂的資料  
  
#### 排序 NamedRange 控制項的資料  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 方法。  下列範例需要工作表上名為 `Fruits` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 將下列程式碼放在 Sheet1.vb 或 Sheet1.cs 中，以排序 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中的資料。  此程式碼假設您在名為 `Sheet1` 的工作表中，有名為 `fruitList` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  
  
#### 排序 ListObject 控制項的資料  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 屬性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## 排序 VSTO 增益集的資料  
  
#### 排序原生範圍的資料  
  
1.  呼叫原生 Excel <xref:Microsoft.Office.Interop.Excel.Range> 控制項的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  下列範例需要工作表上名為 `Fruits` 的原生 Excel 控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### 排序 ListObject 控制項的資料  
  
1.  呼叫原生 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控制項 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 屬性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  下列範例假設使用中工作表有名為 `fruitList` 的原生 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式用遞增 &#40;減&#41; 變化的資料自動填滿範圍](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  