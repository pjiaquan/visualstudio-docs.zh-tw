---
title: "如何：以程式設計方式在搜尋後還原選取 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 還原選取範圍"
  - "搜尋, 之後還原選取範圍"
  - "選取, 搜尋之後還原"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：以程式設計方式在搜尋後還原選取
  如果在文件中尋找和取代文字，您可能想要在完成搜尋後，還原使用者原來的選取範圍。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 範例程序中的程式碼使用兩個 <xref:Microsoft.Office.Interop.Word.Range> 物件。  一個儲存目前的 <xref:Microsoft.Office.Interop.Word.Selection>，另一個則設定整份文件用來做為搜尋範圍。  
  
### 若要在搜尋之後還原使用者原來的選取範圍  
  
1.  為文件和目前選取範圍建立 <xref:Microsoft.Office.Interop.Word.Range> 物件。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#83)]
     [!code-vb[Trin_VstcoreWordAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#83)]  
  
2.  執行搜尋和取代作業。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#84](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#84)]
     [!code-vb[Trin_VstcoreWordAutomation#84](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#84)]  
  
3.  選取開始範圍以還原使用者原來的選取範圍。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#85](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#85)]
     [!code-vb[Trin_VstcoreWordAutomation#85](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#85)]  
  
 下列程式碼範例示範完整的方法：  
  
## 範例  
 [!code-csharp[Trin_VstcoreWordAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#82)]
 [!code-vb[Trin_VstcoreWordAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#82)]  
  
## 請參閱  
 [如何：以程式設計方式在文件中搜尋和取代文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [如何：以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [如何：以程式設計方式在文件中找到的項目之間執行迴圈](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  