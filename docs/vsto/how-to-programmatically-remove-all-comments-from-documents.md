---
title: "如何：以程式設計方式從文件中移除所有的註解 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，移除註解"
  - "註解，從文件移除"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以程式設計方式從文件中移除所有的註解
  您可以使用 DeleteAllComments 方法，從 Microsoft Office Word 文件移除所有註解。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 從屬於文件層級自訂一部分的文件移除所有註解  
  
1.  呼叫您專案中之 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> 方法。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### 使用 VSTO 增益集從文件移除所有註解  
  
1.  呼叫您要從中移除註解之 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> 方法。  
  
     下列程式碼範例會從使用中文件移除所有註解。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## 請參閱  
 [如何：以程式設計方式為文件中的文字加入註解](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)  
  
  