---
title: "如何：以程式設計方式將圖形加入至 Visio 文件 | Microsoft Docs"
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
  - "Visio [Visual Studio 中的 Office 程式開發]，加入 Visio 圖形"
  - "圖形 [Visual Studio 中的 Office 程式開發]，加入 Visio 圖形"
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以程式設計方式將圖形加入至 Visio 文件
  您可以從樣板擷取主圖形並把圖形放在使用中的頁面上，即可在 Microsoft Office Visio 文件中加入圖形。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) 方法、[Microsoft.Office.Interop.Visio.Application.ActivePage](HV10069528) 屬性和 [Microsoft.Office.Interop.Visio.Page.Drop](HV10070273) 方法的 VBA 參考文件。  
  
## 在 Visio 文件中加入圖形  
  
#### 在 Visio 文件中加入圖形  
  
-   以使用中的文件，從 Documents.Masters 集合中擷取主圖形，然後將圖形放在使用中的文件。 您可以使用索引或主圖形名稱來擷取主圖形。  
  
     下列程式碼範例會建立空白的 Visio 文件，然後用停駐的 \[基本圖形\] 樣板開啟它。 程式碼接著會擷取數個圖形，並將它們放在使用中的頁面上。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)   
 [如何：以程式設計方式在 Visio 文件中複製並貼上圖形](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  