---
title: "如何：以程式設計方式關閉文件 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，關閉"
  - "Word [Visual Studio 中的 Office 程式開發]，關閉文件"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 如何：以程式設計方式關閉文件
  您可以關閉使用中文件，或者指定要關閉的文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 關閉使用中的文件  
 有兩種程序可以關閉使用中文件：一個適用於文件層級自訂，而另一個適用於 VSTO 增益集。  
  
#### 關閉文件層級自訂中的使用中文件  
  
1.  呼叫專案中 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.Document.Close%2A> 方法，關閉與自訂相關聯的文件。 若要使用下列程式碼範例，請從 `ThisDocument` 類別執行程式碼。  
  
    > [!NOTE]  
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### 關閉 VSTO 增益集中的使用中文件  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> 屬性的 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法，關閉使用中的文件。 若要使用下列程式碼範例，請從專案的 `ThisAddIn` 類別中執行此範例。  
  
    > [!NOTE]  
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 依指定名稱關閉文件  
 對 VSTO 增益集和文件層級自訂而言，依指定名稱關閉文件的方式都是相同的。  
  
#### 依指定名稱關閉文件  
  
1.  指定文件名稱為 <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> 集合的引數，然後再呼叫 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> 方法。 下列程式碼範例假設在 Word 中開啟了名為 **NewDocument** 的文件。  
  
    > [!NOTE]  
    >  這個範例會將 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 值傳遞給 *SaveChanges* 參數，關閉但不儲存變更或提示使用者。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## 請參閱  
 [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何：以程式設計方式儲存文件](../vsto/how-to-programmatically-save-documents.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  