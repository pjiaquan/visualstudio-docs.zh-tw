---
title: "如何：以程式設計方式列印文件 | Microsoft Docs"
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
  - "Word [Visual Studio 中的 Office 程式開發]，列印文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，列印"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：以程式設計方式列印文件
  您可以將整個 Microsoft Office Word 文件，或文件的一部分，列印到預設印表機。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 印列屬於文件層級自訂一部分的文件  
  
#### 列印整份文件  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Interop.Word.Document> 類別的 `ThisAddIn` 方法來列印整份文件。 若要使用這個範例，請從 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### 列印文件的目前頁面  
  
1.  在專案中呼叫 <xref:Microsoft.Office.Interop.Word.Document> 類別的 `ThisAddIn` 方法，並指定要列印一份目前的頁面。 若要使用這個範例，請從 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## 使用 VSTO 增益集來列印文件  
  
#### 列印整份文件  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word.Document> 物件的 `ThisAddIn` 方法。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### 列印文件的目前頁面  
  
1.  呼叫您要列印之 <xref:Microsoft.Office.Interop.Word.Document> 物件的 `ThisAddIn` 方法，並指定要列印一份目前的頁面。 下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## 請參閱  
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  