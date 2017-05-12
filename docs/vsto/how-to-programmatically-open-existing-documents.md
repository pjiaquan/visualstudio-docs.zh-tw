---
title: "如何：以程式設計方式開啟現有文件"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 開啟"
  - "Word [Visual Studio 中的 Office 程式開發], 開啟文件"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以程式設計方式開啟現有文件
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>方法會開啟以完整路徑名稱和檔名指定的現有 Microsoft Office Word 文件。  此方法傳回 <xref:Microsoft.Office.Interop.Word.Document>，表示已開啟的文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要開啟文件  
  
-   呼叫 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法，並提供文件的路徑。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### 若要以唯讀方式開啟文件  
  
-   呼叫 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 方法、提供文件的路徑，並在方法呼叫中將 *ReadOnly* 引數設定為 **True**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## 編譯程式碼  
 這個程式碼範例需要符合下列條件：  
  
-   名稱為 NewDocument.doc 的文件必須存在於磁碟機 C 中名稱為 Test 的目錄。  
  
## 請參閱  
 [如何：以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)   
 [如何：以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  