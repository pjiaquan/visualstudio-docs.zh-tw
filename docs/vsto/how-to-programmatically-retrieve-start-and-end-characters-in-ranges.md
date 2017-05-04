---
title: "如何：以程式設計方式擷取範圍中的開頭和結尾字元 | Microsoft Docs"
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
  - "範圍，擷取開頭和結尾字元"
  - "結尾字元"
  - "開頭字元"
  - "文件 [Visual Studio 中的 Office 程式開發]，擷取範圍"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 如何：以程式設計方式擷取範圍中的開頭和結尾字元
  這個範例示範如何以字元位置形式，擷取範圍的開始和結尾位置。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要在文件層級自訂中擷取範圍的開始和結尾字元  
  
1.  取得 <xref:Microsoft.Office.Interop.Word.Range> 物件之 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 和 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 屬性的值。 下列程式碼範例會取得文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### 若要使用 VSTO 增益集擷取範圍的開頭和結尾字元  
  
1.  取得 <xref:Microsoft.Office.Interop.Word.Range> 物件之 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 和 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 屬性的值。 下列程式碼範例會取得使用中文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以程式設計方式摺疊文件的範圍或選取的範圍](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以程式設計方式計算文件中的字元數](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  