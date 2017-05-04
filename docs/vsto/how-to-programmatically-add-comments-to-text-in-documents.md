---
title: "如何：以程式設計方式為文件中的文字加入註解 | Microsoft Docs"
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
  - "註解，加入文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，加入註解"
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：以程式設計方式為文件中的文字加入註解
  Document 類別的 Comments 屬性會將註解加入 Microsoft Office Word 文件中某個範圍的文字。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例會將註解加入文件中的第一個段落。  
  
### 若要在文件層級自訂中將新註解加入文字  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 屬性的 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 方法，並提供範圍和註解文字。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomation#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#118)]  
  
### 若要在 VSTO 增益集中將新註解加入文字  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 屬性的 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 方法，並提供範圍和註解文字。  
  
     下列程式碼範例會將註解加入現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#118)]  
  
## 穩固程式設計  
 若要變更 Word 加入註解中的使用者縮寫，請使用 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 屬性。  
  
## 請參閱  
 [如何：以程式設計方式從文件中移除所有的註解](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)  
  
  