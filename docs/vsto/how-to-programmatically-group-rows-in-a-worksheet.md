---
title: "如何：以程式設計方式在工作表中分組資料列 | Microsoft Docs"
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
  - "資料行 [Visual Studio 中的 Office 程式開發], 取消分組"
  - "群組"
  - "群組 [Visual Studio 中的 Office 程式開發], 在工作表中清除"
  - "群組, 在工作表中建立"
  - "範圍, 建立群組"
  - "資料列 [Visual Studio 中的 Office 程式開發], 取消分組"
  - "工作表, 清除群組"
  - "工作表, 建立群組"
  - "工作表, 取消分組資料列和資料行"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式在工作表中分組資料列
  您可以將一個或多個完整資料列組成群組。  若要在工作表中建立群組，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用 NamedRange 控制項  
 如果要在設計階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入至文件層級專案，您可以使用這個控制項，以程式設計方式建立群組。  下列範例假設同一份工作表中有三個 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項：`data2001`、`data2002` 和 `dataAll`。  每個已命名範圍都會參考工作表中的完整資料列。  
  
#### 若要在工作表中建立 NamedRange 控制項群組  
  
1.  對於三個已命名的範圍，呼叫每個範圍的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> 方法，將這三個範圍群組起來：  這段程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  若要取消資料列的群組，請呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> 方法。  
  
## 使用原生 Excel 範圍  
 此程式碼會假設您的工作表上有三個 Excel 範圍，名稱分別是 `data2001`、`data2002` 和 `dataAll`。  
  
#### 若要在工作表中建立 Excel 範圍群組  
  
1.  對於三個已命名的範圍，呼叫每個範圍的 <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> 方法，將這三個範圍群組起來：  下列範例假設同一份工作表中有三個名稱分別為 `data2001`、`data2002` 和 `dataAll` 的 <xref:Microsoft.Office.Interop.Excel.Range> 控制項。  每個已命名範圍都會參考工作表中的完整資料列。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  若要取消資料列的群組，請呼叫 <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> 方法。  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  