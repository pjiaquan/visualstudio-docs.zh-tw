---
title: "如何：以程式設計方式移除工作表的保護 | Microsoft Docs"
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
  - "工作表，取消保護"
  - "文件 [Visual Studio 中的 Office 程式開發]，文件保護"
  - "文件保護，移除工作表的"
  - "Unprotect 方法"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以程式設計方式移除工作表的保護
  您可以程式設計的方式，移除 Microsoft Office Excel 工作表保護。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下例使用的變數 `getPasswordFromUser`，包含從使用者處取得的密碼。  
  
### 取消文件層級自訂工作表的保護  
  
1.  呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> 方法並傳入密碼，如有必要。 這個範例會假設您是使用名為 `Sheet1` 的工作表。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### 取消 VSTO 增益集工作表的保護  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> 方法並傳入密碼，如有必要。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [如何：以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)   
 [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  