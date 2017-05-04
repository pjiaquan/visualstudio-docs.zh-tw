---
title: "如何：以程式設計方式開啟 Visio 文件 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，開啟 Visio 文件"
  - "Visio [Visual Studio 中的 Office 程式開發]，開啟 Visio 文件"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：以程式設計方式開啟 Visio 文件
  開啟現有 Microsoft Office Visio 文件的方法有兩種：Open 和 OpenEx。OpenEx 方法和 Open 方法相同，但是它提供了引數，讓呼叫端在其中指定文件開啟的方式。  
  
 如需此物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456) 方法的 VBA 參考文件。  
  
## 開啟 Visio 文件  
  
#### 開啟 Visio 文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.Open 方法並提供 Visio 文件的完整路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 以指定的引數開啟 Visio 文件  
  
#### 開啟 Visio 文件為唯讀並停駐  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.OpenEx 方法，提供 Visio 文件的完整路徑，以及包含要使用的引數，在本例中為「停駐」和「唯讀」。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## 編譯程式碼  
 這段程式碼範例需要下列項目：  
  
-   在 \[我的文件\] 資料夾 \(Windows XP 及更早版本\) 或 \[文件\] 資料夾 \(Windows Vista\) 中，名為 `Test` 的目錄中必須有名為 `myDrawing.vsd` 的 Visio 文件。  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何：以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何：以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  