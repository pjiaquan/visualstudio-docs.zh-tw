---
title: "如何：以程式設計方式列印 Visio 文件 | Microsoft Docs"
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
  - "Visio [Visual Studio 中的 Office 程式開發]，列印 Visio 文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，列印 Visio 文件"
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以程式設計方式列印 Visio 文件
  您可以列印整份 Microsoft Office Visio 文件，或僅列印特定頁面。  
  
 如需此列印方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Print](HV10070345) 方法和 [Microsoft.Office.Interop.Visio.Page.Print](HV10070404) 方法的 VBA 參考文件。  
  
## 列印 Visio 文件  
  
#### 列印整份文件  
  
-   呼叫您要列印之 Microsoft.Office.Interop.Visio.Document 物件的 Microsoft.Office.Interop.Visio.Document.Print 方法。  
  
     下列程式碼範例會列印使用中的文件。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#8)]  
  
## 列印 Visio 文件頁面  
  
#### 列印文件頁面  
  
-   呼叫您要列印之 Microsoft.Office.Interop.Visio.Pages 物件的 Microsoft.Office.Interop.Visio.Pages.Print 方法。  
  
     下列程式碼範例會列印使用中之文件的第一頁。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何：以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  