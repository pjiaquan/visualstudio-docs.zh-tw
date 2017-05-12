---
title: "如何：以程式設計方式摺疊文件的範圍或選取的範圍"
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
  - "選取範圍，摺疊"
  - "文件 [Visual Studio 中的 Office 程式開發]，折疊範圍"
  - "摺疊選取範圍"
  - "範圍，折疊"
  - "折疊範圍"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以程式設計方式摺疊文件的範圍或選取的範圍
  如果您正在使用 <xref:Microsoft.Office.Interop.Word.Range> 或 <xref:Microsoft.Office.Interop.Word.Selection> 物件，您可能會想要先將選取範圍變更為插入點再插入文字，以免覆寫現有的文字。<xref:Microsoft.Office.Interop.Word.Range> 和 <xref:Microsoft.Office.Interop.Word.Selection> 物件都具有 Collapse 方法，其使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> 列舉值：  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 將選取範圍摺疊至選取範圍的開頭。 如果不指定列舉值，這就是預設值。  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 將選取範圍摺疊至選取範圍的結尾。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 摺疊範圍並插入新的文字  
  
1.  在文件中建立組成第一個段落的 <xref:Microsoft.Office.Interop.Word.Range> 物件。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 列舉值摺疊範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  插入新的文字。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  選取 <xref:Microsoft.Office.Interop.Word.Range>。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 如果使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 列舉值，文字就會插入下列段落的開頭。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 您可能希望將新句子插入在段落標記之前，但實際情況並非如此，因為原始範圍包含了段落標記。 如需詳細資訊，請參閱[如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)。  
  
## 文件層級自訂範例  
  
#### 摺疊文件層級自訂中的範圍  
  
1.  下列範例顯示文件層級自訂的完整方法。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## VSTO 增益集範例  
  
#### 摺疊 VSTO 增益集中的範圍  
  
1.  下列範例顯示 VSTO 增益集的完整方法。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## 請參閱  
 [如何：以程式設計方式在 Word 文件中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式擷取範圍中的開頭和結尾字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  