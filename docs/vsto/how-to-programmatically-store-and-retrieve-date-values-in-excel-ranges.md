---
title: "如何：以程式設計方式在 Excel 範圍中儲存和擷取日期值"
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
  - "日期值"
  - "日期值, 在 Excel 範圍中儲存"
  - "日期, 從 Excel 範圍擷取"
  - "日期, 在 Excel 範圍中儲存"
  - "Excel [Visual Studio 中的 Office 程式開發], 從範圍擷取日期值"
  - "Excel [Visual Studio 中的 Office 程式開發], 在範圍中儲存日期值"
  - "範圍, 擷取日期值"
  - "範圍, 儲存日期值"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：以程式設計方式在 Excel 範圍中儲存和擷取日期值
  您可以在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件中儲存和擷取一些值。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 如果您使用 Visual Studio 中的 Office 開發工具在範圍中儲存 1900 年 1 月 1 日 \(含\) 之後的日期值，則它會儲存為 OLE Automation \(OA\) 格式。  您必須使用 <xref:System.DateTime.FromOADate%2A> 方法擷取 OLE Automation \(OA\) 日期的值。  如果設定的日期早於 1\/1\/1900，則該日期會儲存為字串。  
  
> [!NOTE]  
>  Excel 日期與 OLE Automation 日期在 1900 的前兩個月不同。  如果核取 \[**1904 日期系統**\] 選項，也會有些差異。  下面的程式碼範例不說明這些差異。  
  
## 使用 NamedRange 控制項  
  
-   這是示範文件層級自訂的範例。  下列程式碼必須放在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
#### 若要在已命名的範圍中儲存日期值  
  
1.  在儲存格 \[**A1**\] 建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  將今天日期設為 `NamedRange1` 的值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### 若要擷取已命名範圍中的日期值  
  
1.  擷取 `NamedRange1` 的日期值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## 使用原生 Excel 範圍  
  
#### 若要在原生 Excel 範圍物件中儲存日期值  
  
1.  建立表示 \[**A1**\] 儲存格的 <xref:Microsoft.Office.Interop.Excel.Range>。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  將今天日期設為 `rng` 的值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### 若要從原生 Excel 範圍物件擷取日期值  
  
1.  擷取 `rng` 的日期值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  