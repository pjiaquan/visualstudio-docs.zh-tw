---
title: "如何：以程式設計方式將圖片及文字藝術師加入至文件"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 加入圖片"
  - "圖形, 加入至 Word 文件"
  - "Word 文件, 加入圖片"
  - "Word 文件, 加入文字藝術師"
  - "文字藝術師, 加入至文件"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以程式設計方式將圖片及文字藝術師加入至文件
  您可以在設計階段或執行階段，將圖片和繪圖物件加入至您的文件。  文字藝術師可讓您將裝飾文字加入至 Microsoft Office Word 文件。  這些特殊文字效果是繪圖物件，您可自訂並將它們插入至文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 在設計階段加入圖片  
 如果您正在開發文件層級自訂，可以在設計階段將圖片加入至文件。  
  
#### 在設計階段將圖片加入至 Word 文件  
  
1.  請將游標置於想要在文件中插入圖片的位置。  
  
2.  按一下功能區的 \[插入\] 索引標籤。  
  
3.  按一下 \[插圖\] 群組中的 \[圖片\]。  
  
4.  在 \[插入圖片\] 對話方塊中，巡覽至想要插入的圖片，並按一下 \[插入\]。  
  
     圖片隨即加入文件中目前的游標位置。  
  
## 在執行階段加入圖片  
 您可以將圖片插入文件中目前游標的位置。  
  
#### 在游標位置加入圖片  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word.InlineShapes> 集合的 <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> 方法，並傳入檔案的名稱。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## 在設計階段加入文字藝術師  
 如果您正在開發文件層級自訂，可以在設計階段將文字藝術師加入至文件。  
  
#### 在設計階段將文字藝術師加入至 Word 文件  
  
1.  請將游標置於想要在文件中插入文字藝術師的位置。  
  
2.  按一下功能區的 \[插入\] 索引標籤。  
  
3.  按一下 \[文字\] 群組中的 \[文字藝術師\]，然後選取文字藝術師樣式。  
  
4.  將想要在文件中顯示的文字加入至 \[編輯文字藝術師文字\] 對話方塊，並按一下 \[確定\]。  
  
     加入至文件的文字即會套用選取的文字藝術師樣式。  
  
## 在執行階段加入文字藝術師  
 您可以將文字藝術師插入至文件中目前游標的位置。  文件層級自訂與 VSTO 增益集的程序不同。  
  
#### 在文件層級自訂的游標位置加入文字藝術師  
  
1.  取得目前游標位置的左端和頂端位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  請呼叫文件中 <xref:Microsoft.Office.Interop.Word.Shapes> 物件的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### 在 VSTO 增益集的游標位置加入文字藝術師  
  
1.  取得目前游標位置的左端和頂端位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  請呼叫使用中文件 \(或您所指定的不同文件\) 之 <xref:Microsoft.Office.Interop.Word.Shapes> 物件的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## 編譯程式碼  
  
-   C 磁碟機上必須存在名為 **SamplePicture.jpg** 的圖片。  
  
## 請參閱  
 [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以程式設計方式在 Word 文件中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以程式設計方式在搜尋後還原選取](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [如何：以程式設計方式儲存文件](../vsto/how-to-programmatically-save-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  