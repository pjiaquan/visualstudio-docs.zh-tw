---
title: "如何：以程式設計方式保護文件及部分的文件"
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
  - "文件保護"
  - "文件 [Visual Studio 中的 Office 程式開發]，文件保護"
  - "Word 文件，保護"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：以程式設計方式保護文件及部分的文件
  您可以在 Microsoft Office Word 文件加入保護，以防止使用者對文件進行任何編輯。  
  
 `ThisAddIn`  
  
 您也可以將文件的特定區域標記為例外狀況，讓指定的使用者只能編輯文件的那些區域。 例如，您可能想要保護除了特定書籤以外的整份文件。 您可以選擇性地加入密碼，除非使用者知道密碼，否則無法移除文件保護。  
  
> [!NOTE]  
>  下列範例不會使用密碼保護。不過，您可以考慮在加入文件保護時使用密碼。 如需詳細資訊，請參閱文件保護裝置範例：`ThisAddIn`。  
  
 您也可以使用內容控制項保護文件的部分。 如需詳細資訊，請參閱`ThisAddIn`。  
  
## 保護屬於文件層級自訂一部分的文件  
  
#### 保護屬於文件層級自訂一部分的文件  
  
1.  呼叫您專案中之 <xref:Microsoft.Office.Interop.Word.Document> 類別的 `ThisAddIn` 方法。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### 從文件保護排除書籤控制項  
  
1.  使用 `ThisAddIn` 方法保護整份文件。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  從文件保護排除 `ThisAddIn`。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### 編譯程式碼  
 若要使用這些程式碼範例，請從專案的 `ThisAddIn` 類別中執行它們。 這些程式碼範例假設您在這段程式碼出現的文件中，已有現有的 `ThisAddIn` 控制項，名為 <xref:Microsoft.Office.Interop.Word.Document>。  
  
## 使用 VSTO 增益集來保護文件  
  
#### 使用應用程式層級 VSTO 增益集來保護文件  
  
1.  呼叫您要保護之 <xref:Microsoft.Office.Interop.Word.Document> 的 `ThisAddIn` 方法。  
  
     下列程式碼範例會保護使用中文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## 請參閱  
 [文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何：允許程式碼在具有限制使用權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [如何：將書籤控制項加入至 Word 文件](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  