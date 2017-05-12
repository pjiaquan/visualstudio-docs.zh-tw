---
title: "如何：以程式設計方式隱藏工作表"
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
  - "隱藏的工作表"
  - "工作表，隱藏"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以程式設計方式隱藏工作表
  您可以顯示或隱藏活頁簿中的任何工作表。 若要隱藏工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用工作表主項目  
 如果在文件層級自訂的設計階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 屬性隱藏指定的工作表。  
  
#### 使用工作表主項目隱藏工作表  
  
1.  將 `Sheet1` 主項目的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## 使用 Excel 活頁簿的工作表集合  
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：  
  
-   您要隱藏 VSTO 增益集的工作表。  
  
-   您想要隱藏的工作表，是在文件層級自訂的執行階段建立的。  
  
#### 使用 Excel 活頁簿的工作表集合隱藏工作表  
  
1.  將工作表的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以程式設計方式在活頁簿內移動工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  