---
title: "如何：以程式設計方式跨工作表複製資料和格式"
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
  - "複製資料, Visual Studio 中的 Office 程式開發"
  - "資料 [Visual Studio 中的 Office 程式開發], 跨工作表複製"
  - "格式化 [Visual Studio 中的 Office 程式開發]"
  - "工作表, 複製資料"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 如何：以程式設計方式跨工作表複製資料和格式
  您可以使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> 方法，將工作表上某個範圍的資料複製到活頁簿中的所有其他工作表。  請指定範圍，並指定您是要複製資料、格式還是兩者都要複製。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## 編譯程式碼  
 這個範例需要工作表中有名為 `rangeData` 的範圍。  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何：以程式設計方式在包含選取儲存格的工作表列中變更格式](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  