---
title: "如何：以程式設計方式在 Word 中設定搜尋選項"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 搜尋選項"
  - "搜尋, Word 選項"
  - "設定, Word 搜尋選項"
  - "Word, 搜尋選項"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式在 Word 中設定搜尋選項
  有兩種方法可以針對 Microsoft Office Word 文件中的選取範圍設定搜尋選項：  
  
-   設定 <xref:Microsoft.Office.Interop.Word.Find> 物件的個別屬性。  
  
-   在 <xref:Microsoft.Office.Interop.Word.Find> 物件的 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法中使用引數。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 使用 Find 物件的屬性  
 下列程式碼會設定 <xref:Microsoft.Office.Interop.Word.Find> 物件的屬性，以在目前選取範圍內搜尋文字。  請注意，搜尋準則 \(例如向前搜尋、換行和搜尋文字等\) 都是 <xref:Microsoft.Office.Interop.Word.Find> 物件的屬性。  
  
 設定 <xref:Microsoft.Office.Interop.Word.Find> 物件的每項屬性不適用於撰寫 C\# 程式碼的情況，因為您必須指定相同的屬性做為 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的參數。  因此，這個範例只包含 Visual Basic 程式碼。  
  
#### 若要使用 Find 物件設定搜尋選項  
  
1.  設定 <xref:Microsoft.Office.Interop.Word.Find> 物件的屬性，以在選取範圍中向前搜尋 **find me** 文字。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## 使用 Execute 方法引數  
 下列程式碼會使用 <xref:Microsoft.Office.Interop.Word.Find> 物件的 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法，搜尋目前選取範圍內的文字。  請注意，這個程式碼會傳遞搜尋準則 \(例如向前搜尋、換行和搜尋文字等\)，以做為 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的參數。  
  
#### 若要使用 Execute 方法引數設定搜尋選項  
  
1.  傳遞搜尋準則，做為 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法的參數，以便在選取範圍中向前搜尋 **find me** 文字。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中搜尋和取代文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何：以程式設計方式在文件中找到的項目之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [如何：以程式設計方式在搜尋後還原選取](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  