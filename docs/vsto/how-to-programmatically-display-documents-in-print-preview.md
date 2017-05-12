---
title: "如何：以程式設計方式在預覽列印中顯示文件"
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
  - "Word [Visual Studio 中的 Office 程式開發]，在預覽列印中顯示文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，在預覽列印中顯示"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：以程式設計方式在預覽列印中顯示文件
  如果您的方案會產生報告，您可能想要在 \[預覽列印\] 模式中向使用者顯示報告。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 文件層級自訂的程序  
  
#### 呼叫 PrintPreview 方法以在預覽列印中顯示文件  
  
1.  請呼叫 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> 方法。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### 設定 PrintPreview 屬性以在預覽列印中顯示文件  
  
1.  將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## VSTO 增益集的程序  
  
#### 呼叫 PrintPreview 方法以在預覽列印中顯示文件  
  
1.  呼叫您要預覽之 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> 方法。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### 設定 PrintPreview 屬性以在預覽列印中顯示文件  
  
1.  將 <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Application> 屬性設定為 **true**。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## 請參閱  
 [如何：以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)   
 [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以程式設計方式建立新文件](../vsto/how-to-programmatically-create-new-documents.md)  
  
  