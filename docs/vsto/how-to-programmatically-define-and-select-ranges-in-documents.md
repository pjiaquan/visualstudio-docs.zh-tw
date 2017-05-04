---
title: "如何：以程式設計方式在文件中定義及選取範圍 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 範圍"
  - "文件 [Visual Studio 中的 Office 程式開發], 選取句子"
  - "範圍, 在文件中定義"
  - "範圍, 在文件中選取"
  - "句子, 在文件中選取"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式在文件中定義及選取範圍
  您也可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件定義 Microsoft Office Word 文件中的範圍。  您可以使用數種方式來選取整份文件，例如，使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法，或是使用 <xref:Microsoft.Office.Tools.Word.Document> 類別 \(在文件層級自訂中\) 或 <xref:Microsoft.Office.Interop.Word.Document> 類別 \(在 VSTO 增益集中\) 的 Content 屬性。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 定義範圍  
 下列範例示範如何建立包含使用中文件中前七個字元 \(包括非列印字元\) 的新 <xref:Microsoft.Office.Interop.Word.Range> 物件。  它接著會選取範圍內的文字。  
  
#### 定義文件層級自訂中的範圍  
  
1.  將開始和結束字元傳遞給 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Range%2A> 方法，以將範圍新增至文件。  若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### 使用 VSTO 增益集定義範圍  
  
1.  將開始和結束字元傳遞給 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Range%2A> 方法，以將範圍新增至文件。  下列程式碼範例會將範圍新增至使用中文件。  若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## 選取文件層級自訂中的範圍  
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性來選取整份文件。  
  
#### 使用 Select 方法將整份文件選取為範圍  
  
1.  使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。  若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### 使用內容屬性將整份文件選取為範圍  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性定義包含整份文件的範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 您也可以使用其他物件的方法和屬性來定義範圍。  
  
#### 選取使用中文件中的句子  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。  使用您想要選取之句子的索引。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 另一種選取句子的方法是手動設定範圍的開始和結束值。  
  
#### 手動設定開始和結束值來選取句子  
  
1.  建立範圍變數。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  檢查文件中是否至少有兩個句子，並設定範圍的 *Start* 和 *End* 引數，然後選取範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## 使用 VSTO 增益集選取範圍  
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性來選取整份文件。  
  
#### 使用 Select 方法將整份文件選取為範圍  
  
1.  使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。  下列程式碼範例會選取使用中文件的內容。  若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### 使用內容屬性將整份文件選取為範圍  
  
1.  使用 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性定義包含整份文件的範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 您也可以使用其他物件的方法和屬性來定義範圍。  
  
#### 選取使用中文件中的句子  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。  使用您想要選取之句子的索引。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 另一種選取句子的方法是手動設定範圍的開始和結束值。  
  
#### 手動設定開始和結束值來選取句子  
  
1.  建立範圍變數。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  檢查文件中是否至少有兩個句子，並設定範圍的 *Start* 和 *End* 引數，然後選取範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## 請參閱  
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式擷取範圍中的開頭和結尾字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以程式設計方式摺疊文件的範圍或選取的範圍](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  