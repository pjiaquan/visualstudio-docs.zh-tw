---
title: "如何：以程式設計方式在 Word 文件中插入文字 | Microsoft Docs"
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
  - "範圍，在文件中插入文字"
  - "文字 [Visual Studio 中的 Office 程式開發]，在文件中插入"
  - "範圍，取代文件中的文字"
  - "文件 [Visual Studio 中的 Office 程式開發]，插入文字"
  - "文字 [Visual Studio 中的 Office 程式開發]，取代"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 如何：以程式設計方式在 Word 文件中插入文字
  在 Microsoft Office Word 文件中插入文字的方式主要有三種：  
  
-   在範圍中插入文字。  
  
-   以新文字取代範圍中的文字。  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Selection> 物件的 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 方法將文字插入游標或選取範圍。  
  
> [!NOTE]  
>  您也可以將文字插入內容控制項與書籤中。 如需詳細資訊，請參閱 [內容控制項](../vsto/content-controls.md) 與 [書籤控制項](../vsto/bookmark-control.md)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 在範圍中插入文字  
 使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性將文字插入文件。  
  
#### 若要在範圍中插入文字  
  
1.  在文件的開頭指定範圍，並插入文字 **New Text**。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  選取 <xref:Microsoft.Office.Interop.Word.Range> 物件，這時物件已從一個字元擴展為所插入文字的長度。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## 取代範圍中的文字  
 如果指定的範圍包含文字，則範圍內的所有文字都會以插入的文字取代。  
  
#### 若要取代範圍中的文字  
  
1.  建立一個包含文件中前 12 個字元的 <xref:Microsoft.Office.Interop.Word.Range> 物件。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  以 **New Text** 字串取代這些字元。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  選取範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## 使用 TypeText 插入文字  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 方法會在選取範圍插入文字。<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 的行為方式會因使用者電腦上設定的選項而異。 下列程序中的程式碼宣告了 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數，並且關閉 **Overtype** 選項 \(如果是開啟的\)。 如果啟用 **Overtype** 選項，則會覆寫游標後面的任何文字。  
  
#### 若要使用 TypeText 方法插入文字  
  
1.  宣告 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  關閉 **Overtype** 選項 \(如果是開啟的\)。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  測試目前的選取範圍是否為插入點。  
  
     如果是，程式碼就會使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 插入句子，然後使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> 方法插入段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  **ElseIf** 區塊中的程式碼會進行測試，檢查選取範圍是否為一般的選取範圍。 如果是，則另一個 **If** 區塊就會測試 **ReplaceSelection** 選項是否已開啟。 如果該選項已開啟，程式碼就會使用選取範圍的 <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> 方法，將選取範圍摺疊至文字選取區塊起始處的插入點。 插入文字和段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  如果選取範圍不是插入點或選取文字的區塊，則 **Else** 區塊中的程式碼不會執行任何動作。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 您也可以使用 <xref:Microsoft.Office.Interop.Word.Selection> 物件的 <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> 方法，這個方法會模仿鍵盤上退格鍵 \(BACKSPACE\) 的功能。 但是，如果要插入和處理文字，<xref:Microsoft.Office.Interop.Word.Range> 物件可以讓您有更多的控制能力。  
  
 下列範例顯示完整程式碼。 若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行程式碼。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中設定文字格式](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  