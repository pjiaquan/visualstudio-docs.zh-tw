---
title: "如何：以程式設計方式使用 Word 中的內建對話方塊 | Microsoft Docs"
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
  - "Word [Visual Studio 中的 Office 程式開發]，對話方塊"
  - "對話方塊，Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 如何：以程式設計方式使用 Word 中的內建對話方塊
  在使用 Microsoft Office Word 的時候，您有時需要顯示對話方塊讓使用者進行輸入。  雖然您可以自行建立，不過也可以使用 Word 中的內建對話方塊，這些對話方塊是公開在 <xref:Microsoft.Office.Interop.Word.Application> 物件的 <xref:Microsoft.Office.Interop.Word.Dialogs> 集合中。  您可以存取超過 200 種以上以列舉型別 \(Enumeration\) 表示的內建對話方塊。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 顯示對話方塊  
 若要顯示對話方塊，請使用其中一個 <xref:Microsoft.Office.Interop.Word.WdWordDialog> 列舉值來建立 <xref:Microsoft.Office.Interop.Word.Dialog> 物件，以表示您要顯示的對話方塊。  然後，呼叫 <xref:Microsoft.Office.Interop.Word.Dialog> 物件的 <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> 方法。  
  
 下列程式碼範例示範如何顯示 \[**開啟舊檔**\] 對話方塊。  若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### 存取透過晚期繫結使用的對話方塊成員  
 Word 中對話方塊的部分屬性和方法只能透過晚期繫結才能使用。  在 Visual Basic 專案 **Option Strict** 位置開啟，您必須使用反映才能存取這些成員。  如需詳細資訊，請參閱[Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。  
  
 下列程式碼範例在 **Option Strict** 或在開啟以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Visual Basic 專案示範如何使用 \[**開啟的檔案。**\] 對話方塊的 **Name** 屬性。  若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 下列程式碼範例示範如何使用反映來存取 \[**開啟的檔案。**\] 對話方塊的 **Name** 屬性在 **Option Strict** 開啟的 Visual Basic 專案的。  若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 請參閱  
 [如何：以程式設計方式在隱藏模式中使用 Word 對話方塊](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 &#40;C&#35; 和 Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  