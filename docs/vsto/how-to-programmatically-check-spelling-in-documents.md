---
title: "如何：以程式設計方式在文件中檢查拼字"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 檢查拼字"
  - "拼字檢查程式, 文件"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：以程式設計方式在文件中檢查拼字
  若要檢查文件中的拼字，請使用 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法。  這個方法會傳回布林 \(Boolean\) 值，指出所提供的參數是否使用正確的拼寫。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要檢查拼字並將結果顯示在訊息方塊中  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> 方法，並將文字的範圍傳遞給該方法，以檢查拼字錯誤。  若要使用這個程式碼範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  