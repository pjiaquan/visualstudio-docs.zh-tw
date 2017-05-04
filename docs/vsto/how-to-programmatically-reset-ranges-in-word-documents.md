---
title: "如何：以程式設計方式在 Word 文件中重設範圍 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，重設範圍"
  - "範圍，在文件中重設"
ms.assetid: 45ea9434-e548-4d24-938f-4f1ffa5010d0
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以程式設計方式在 Word 文件中重設範圍
  使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 方法，可以調整 Microsoft Office Word 文件中現有範圍的大小。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要重設現有範圍  
  
1.  以文件中前七個字元的開頭設定初始範圍。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#43)]  
  
     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#43)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A>從第二個句子開始設定這個範圍，一直到第五個句子的結尾結束。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#44)]
     [!code-vb[Trin_VstcoreWordAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#44)]  
  
## 文件層級自訂範例  
  
#### 若要重設文件層級自訂中的現有範圍  
  
1.  下列範例顯示文件層級自訂的完整範例。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#42)]  
  
## VSTO 增益集範例  
  
#### 若要重設 VSTO 增益集中的現有範圍  
  
1.  下列範例顯示 VSTO 增益集的完整範例。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#42)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式擷取範圍中的開頭和結尾字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何：以程式設計方式摺疊文件的範圍或選取的範圍](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  