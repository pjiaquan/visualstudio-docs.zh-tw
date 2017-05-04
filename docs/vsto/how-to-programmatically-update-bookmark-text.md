---
title: "如何：以程式設計方式更新書籤文字 | Microsoft Docs"
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
  - "書籤控制項, 更新內容"
  - "書籤, 更新文字"
  - "文字 [Visual Studio 中的 Office 程式開發], 在書籤中更新"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式更新書籤文字
  您可以在 Microsoft Office Word 文件的預留位置書籤中插入文字，以便稍後擷取文字，或取代書籤中的文字。  如果開發的是文件層級自訂，您也可以更新繫結至資料的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項文字。  如需詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 書籤物件可以是下列兩種類型之一：  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> 主控制項。  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項透過啟用資料繫結和公開事件，擴充原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。  如需主控制項的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
-   原生 <xref:Microsoft.Office.Interop.Word.Bookmark> 物件。  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark> 物件沒有事件或資料繫結功能。  
  
 當您指派文字到書籤時，<xref:Microsoft.Office.Interop.Word.Bookmark> 和 <xref:Microsoft.Office.Tools.Word.Bookmark> 的行為不同。  如需詳細資訊，請參閱[書籤控制項](../vsto/bookmark-control.md)。  
  
## 使用主控制項  
  
#### 使用書籤控制項更新書籤內容  
  
1.  建立採用 `bookmark` 引數作為書籤名稱，並採用 `newText` 引數作為要指派給 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性之字串的程序。  
  
    > [!NOTE]  
    >  指派文字給 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 或 <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> 屬性，將不會刪除書籤。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  將 *newText* 字串指派給 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> 屬性。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## 使用 Word 物件  
  
#### 使用 Word 書籤物件更新書籤內容  
  
1.  建立以 `bookmark` 引數作為 <xref:Microsoft.Office.Interop.Word.Bookmark> 的名稱，並以 `newText` 引數作為要指派給 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性之字串的程序。  
  
    > [!NOTE]  
    >  將文字指派給原生 Word <xref:Microsoft.Office.Interop.Word.Bookmark> 物件會刪除書籤。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  將 *newText* 字串指派給書籤的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性，會自動刪除書籤。  然後重新將書籤加入 <xref:Microsoft.Office.Interop.Word.Bookmarks> 集合。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     下列程式碼範例可用於 VSTO 增益集。  本範例使用使用中文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## 請參閱  
 [如何：以程式設計方式在 Word 文件中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [書籤控制項](../vsto/bookmark-control.md)  
  
  