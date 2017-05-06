---
title: "如何：以程式設計方式在文件中加入頁首和頁尾"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 加入頁尾"
  - "文件 [Visual Studio 中的 Office 程式開發], 加入頁首"
  - "頁尾, 加入至文件"
  - "頁首, 加入至 Office 文件"
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以程式設計方式在文件中加入頁首和頁尾
  您可以使用 <xref:Microsoft.Office.Interop.Word.Section> 的 <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> 屬性和 <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> 屬性，將文字加入文件的頁首和頁尾。  文件的每個區段都包含三個頁首和頁尾：  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 文件層級自訂與 VSTO 增益集的程序不同。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 文件層級自訂  
 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行範例。  
  
#### 將文字加入文件的頁尾  
  
1.  下列程式碼範例會設定文件每個區段的主要頁尾要插入的文字字型，然後將文字插入頁尾。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomation#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#114)]  
  
#### 將文字加入文件的頁首  
  
1.  下列程式碼範例會在文件的每個頁首加入顯示頁碼的欄位，然後設定段落對齊方式，讓文字向頁首的右邊靠齊。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomation#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#116)]  
  
## VSTO 增益集  
 若要使用下列程式碼範例，請從專案的 `ThisAddIn` 類別中執行範例。  
  
#### 將文字加入文件的頁尾  
  
1.  下列程式碼範例會設定文件每個區段的主要頁尾要插入的文字字型，然後將文字插入頁尾。  這個程式碼範例使用使用中文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#114)]  
  
#### 將文字加入文件的頁首  
  
1.  下列程式碼範例會在文件的每個頁首加入顯示頁碼的欄位，然後設定段落對齊方式，讓文字向頁首的右邊靠齊。  這個程式碼範例使用使用中文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#116)]  
  
## 請參閱  
 [如何：以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在文件中找到的項目之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
  
  