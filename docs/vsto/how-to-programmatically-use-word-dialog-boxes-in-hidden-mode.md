---
title: "如何：以程式設計方式在隱藏模式中使用 Word 對話方塊 | Microsoft Docs"
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
  - "對話方塊, Word 中的隱藏模式"
  - "隱藏的對話方塊"
  - "Word [Visual Studio 中的 Office 程式開發], 對話方塊"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以程式設計方式在隱藏模式中使用 Word 對話方塊
  您可以只使用一次方法呼叫來執行複雜的作業，方法是叫用 \(Invoke\) Microsoft Office Word 中的內建對話方塊，但不向使用者顯示對話方塊。  使用 <xref:Microsoft.Office.Interop.Word.Dialog> 物件的 <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> 方法，但不呼叫 <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> 方法，即可達此目的。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 範例  
 下列程式碼範例示範如何以隱藏模式，使用 \[**版面設定**\] 對話方塊來設定多個版面設定屬性，而不需要使用者輸入。  這個範例使用 <xref:Microsoft.Office.Interop.Word.Dialog> 物件來設定自訂頁面大小。  版面設定的特定設定 \(例如上邊界、下邊界等\) 都可以做為 <xref:Microsoft.Office.Interop.Word.Dialog> 物件的晚期繫結屬性。  Word 會在執行階段動態建立這些屬性。  
  
 下列範例示範如何在關閉 **Option Strict** 的 Visual Basic 專案或目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 的 Visual C\# 專案中執行這項工作。  在這些專案中，您可以使用 Visual Basic 和 Visual C\# 編譯器中的晚期繫結功能。  若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 下列範例會 **Option Strict** 開啟的 Visual Basic 專案示範如何執行這項工作。  在這些專案中，您必須使用反映才能存取晚期繫結屬性。  若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## 請參閱  
 [如何：以程式設計方式使用 Word 中的內建對話方塊](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)   
 [反映 &#40;C&#35; 和 Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  