---
title: "如何：以程式設計方式在文件中隱藏文字"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，隱藏文字"
  - "文字 [Visual Studio 中的 Office 程式開發]，在文件中隱藏"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：以程式設計方式在文件中隱藏文字
  您可以針對文字的特定範圍設定 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 的 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 屬性，以隱藏文件中的文字。  
  
 例如，您可以暫時隱藏 <xref:Microsoft.Office.Tools.Word.Bookmark> \(文件層級自訂\) 或 <xref:Microsoft.Office.Interop.Word.Bookmark> \(VSTO 增益集\) 內的文字，再將文件傳送至印表機。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 在列印文件時隱藏書籤控制項中的文字  
  
1.  建立隱藏指定範圍內所有文字的程序。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  建立取消隱藏指定範圍內所有文字的程序。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  將書籤範圍傳遞給 `HideText` 方法、列印文件，然後將相同範圍傳遞給 `UnhideText` 方法。  
  
     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## 編譯程式碼  
 這個程式碼範例假設文件包含名為 `bookmark1` 的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項 \(文件層級自訂\) 或 <xref:Microsoft.Office.Interop.Word.Bookmark> 控制項 \(VSTO 增益集\)。  
  
## 請參閱  
 [如何：以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)   
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以程式設計方式更新書籤文字](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  