---
title: "如何：以程式設計方式在文件中設定文字格式"
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
  - "格式化 [Visual Studio 中的 Office 程式開發]"
  - "文件 [Visual Studio 中的 Office 程式開發]，格式化文字"
  - "文字 [Visual Studio 中的 Office 程式開發]，文件中的格式化"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以程式設計方式在文件中設定文字格式
  您可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件格式化 Microsoft Office Word 文件中的文字。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例會選取文件中的第一個段落，並變更字型大小、字型名稱和對齊方式。 它接著會選取範圍，並顯示訊息方塊以在執行下個區塊的程式碼之前暫停。 下一個區段呼叫 <xref:Microsoft.Office.Tools.Word.Document> 主項目 \(適用於文件層級自訂\) 或 <xref:Microsoft.Office.Interop.Word.Document> 類別 \(適用於 VSTO 增益集\) 的 Undo 方法三次。 它套用一般縮排樣式，並顯示訊息方塊以暫停程式碼。 接著，程式碼會呼叫 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 方法一次，並顯示訊息方塊。  
  
## 文件層級自訂範例  
  
#### 使用文件層級自訂格式化文字  
  
1.  下列範例可以用於文件層級自訂。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## VSTO 增益集範例  
  
#### 使用 VSTO 增益集格式化文字  
  
1.  下列範例可以用於 VSTO 增益集。 本範例使用現用文件。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以程式設計方式在文件中搜尋和取代文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  