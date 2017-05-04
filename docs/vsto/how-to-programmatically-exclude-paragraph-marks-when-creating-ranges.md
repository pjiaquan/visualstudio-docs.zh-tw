---
title: "如何：以程式設計方式在建立範圍時排除段落標記 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，排除段落"
  - "範圍，在 Word 中排除段落標記"
  - "文件 [Visual Studio 中的 Office 程式開發]，段落標記"
  - "段落，控制結構"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 如何：以程式設計方式在建立範圍時排除段落標記
  每當您根據段落建立 <xref:Microsoft.Office.Interop.Word.Range> 物件時，所有的非列印字元 \(如段落標記\) 都會包含在範圍中。 您可以將文字從來源段落插入目的段落。 如果您不想將目的段落分割成個別段落，則必須先移除來源段落的段落標記。 此外，因為段落格式化資訊儲存在段落標記內，所以在將範圍插入現有段落時，您可能不想包含該資訊。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例程序會宣告兩個字串變數，擷取現用文件的第一段和第二段內容，然後交換它們的內容。 下列範例示範使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法，從範圍移除段落標記，並在段落內插入文字。  
  
### 若要在插入文字時控制段落結構  
  
1.  針對第一和第二個段落建立兩個範圍變數，然後使用 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性擷取其內容。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     下列程式碼範例可用於應用程式層級的 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  指派 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性，並將這兩個段落的文字互換。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  依次選取每個範圍並暫停，以在訊息方塊中顯示結果。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法調整 `firstRange`，讓段落標記不再是 `firstRange` 的一部分。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  取代第一段中的其餘文字，指派新字串給該範圍的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  取代 `secondRange` 中的文字，包括段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  選取 `firstRange` 並暫停，以在訊息方塊中顯示結果，然後對 `secondRange` 執行同樣的動作。  
  
     因為已重新定義 `firstRange` 來排除段落標記，所以會保留段落的原始格式。 不過，`secondRange` 中的段落標記上插入了句子，所以移除了個別段落。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     這兩個範圍的原始內容都儲存為字串，所以您可以將文件還原成原始狀態。  
  
8.  使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法移動一個字元位置，以重新調整 `firstRange`，讓它包含段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. 刪除 `secondRange`。 這會將段落三還原為原始的位置。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. 還原 `firstRange` 中原始段落文字。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. 使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> 方法，將原來第二段的內容插入 `firstRange` 之後，然後選取 `firstRange`。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## 文件層級自訂範例  
  
#### 若要在文件層級自訂中插入文字時控制段落結構  
  
1.  下列範例顯示文件層級自訂的完整方法。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## VSTO 增益集範例  
  
#### 若要在 VSTO 增益集中插入文字時控制段落結構  
  
1.  下列範例顯示 VSTO 增益集的完整方法。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式摺疊文件的範圍或選取的範圍](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何：以程式設計方式在文件中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  