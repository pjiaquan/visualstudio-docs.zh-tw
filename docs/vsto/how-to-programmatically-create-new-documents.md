---
title: "如何：以程式設計方式建立新文件"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 建立"
  - "範本 [Visual Studio 中的 Office 程式開發], 自訂文件"
  - "Word [Visual Studio 中的 Office 程式開發], 建立文件"
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# 如何：以程式設計方式建立新文件
  當您以程式設計方式建立文件時，新的文件就是原生的 <xref:Microsoft.Office.Interop.Word.Document> 物件。  這個物件沒有 <xref:Microsoft.Office.Tools.Word.Document> 主項目的其他事件和資料繫結功能。  如需詳細資訊，請參閱[主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 當您開發文件層級專案時，您無法以程式設計方式在專案中加入 <xref:Microsoft.Office.Tools.Word.Document> 主項目。  在 VSTO 增益集專案中，您可以在執行階段將任何 <xref:Microsoft.Office.Interop.Word.Document> 物件轉換成 <xref:Microsoft.Office.Tools.Word.Document> 主項目。  如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### 根據 Normal 範本建立新文件  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法，根據 Normal 範本建立新文件。  若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreWordAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#1)]  
  
## 使用自訂範本  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法有選擇性的 *Template* 引數，可根據 Normal 範本以外的範本建立新文件。  您必須提供範本的檔案名稱和完整路徑。  
  
#### 根據自訂範本建立新文件  
  
-   呼叫 <xref:Microsoft.Office.Interop.Word.Documents> 集合的 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 方法，並指定範本的路徑。  若要使用這個程式碼範例，請從專案的 `ThisDocument` 或 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreWordAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#2)]  
  
## 請參閱  
 [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  