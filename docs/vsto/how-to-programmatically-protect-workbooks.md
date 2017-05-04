---
title: "如何：以程式設計方式保護活頁簿 | Microsoft Docs"
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
  - "文件保護, 加入至活頁簿"
  - "文件保護, 從活頁簿移除"
  - "文件 [Visual Studio 中的 Office 程式開發], 文件保護"
  - "活頁簿, 密碼"
  - "活頁簿, 保護"
  - "活頁簿, 取消保護"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以程式設計方式保護活頁簿
  您可以保護 Microsoft Office Excel 活頁簿，讓使用者無法加入或刪除工作表，也可以用程式設計的方式取消保護活頁簿。  您可以選擇性地指定密碼，指出是否要保護這個結構 \(讓使用者無法四處移動工作表\) 以及是否要保護活頁簿的視窗。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 保護活頁簿並不會阻礙使用者編輯儲存格。  若要保護資料，您必須保護工作表。  如需詳細資訊，請參閱[如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)。  
  
 下列的程式碼範例會使用變數來包含從使用者處取得的密碼。  
  
## 保護屬於文件層級自訂一部分的活頁簿  
  
#### 若要保護活頁簿  
  
1.  呼叫活頁簿的 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 方法，並加入密碼。  若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼，而不是在工作表類別中執行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### 若要取消保護活頁簿  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> 方法，如果需要密碼則傳遞密碼：  若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼，而不是在工作表類別中執行。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## 使用應用程式層級增益集保護活頁簿  
  
#### 若要保護活頁簿  
  
1.  呼叫活頁簿的 <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> 方法，並加入密碼。  這個程式碼範例會使用現用活頁簿。  若要使用這個範例，請從專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### 若要取消保護活頁簿  
  
1.  呼叫現用活頁簿的 <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> 方法，如果需要密碼則傳遞密碼。  若要使用這個範例，請從專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  