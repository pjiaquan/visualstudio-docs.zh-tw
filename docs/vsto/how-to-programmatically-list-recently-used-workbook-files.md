---
title: "如何：以程式設計方式列出最近使用的活頁簿檔案 | Microsoft Docs"
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
  - "Excel [Visual Studio 中的 Office 程式開發], 列出最近用過的檔案"
  - "最近使用的檔案清單, Excel"
  - "RecentFiles 屬性"
  - "活頁簿, 列出最近用過的"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以程式設計方式列出最近使用的活頁簿檔案
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> 屬性會傳回一個字串集合，其中包含 Microsoft Office Excel 最近使用的檔案清單中出現的所有檔案名稱。  清單的長度會依使用者所選取要保留的檔案數目而變動。  您可以在某個範圍中顯示結果。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 若要在範圍物件中列出最近使用的活頁簿  
  
1.  針對最近使用的檔案清單執行迴圈，並在與 <xref:Microsoft.Office.Interop.Excel.Range> 物件相關的儲存格中顯示那些名稱。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  