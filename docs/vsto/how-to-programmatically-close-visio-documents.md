---
title: "如何：以程式設計方式關閉 Visio 文件 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，關閉 Visio 文件"
  - "Visio [Visual Studio 中的 Office 程式開發]，關閉 Visio 文件"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：以程式設計方式關閉 Visio 文件
  您可以使用 Microsoft.Office.Interop.Visio.Document.Close 方法來關閉使用中的 Microsoft Office Visio 文件。  
  
 如需這個方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Close](HV10070225) 方法的 VBA 參考文件。  
  
## 關閉使用中的文件  
  
#### 關閉使用中的文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Document.Close 方法，關閉使用中的文件。  
  
     若要使用下列程式碼範例，請在 Visio VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何：以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  