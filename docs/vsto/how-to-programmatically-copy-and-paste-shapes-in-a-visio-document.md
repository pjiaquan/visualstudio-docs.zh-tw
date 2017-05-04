---
title: "如何：以程式設計方式在 Visio 文件中複製並貼上圖形 | Microsoft Docs"
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
  - "圖形 [Visual Studio 中的 Office 程式開發]，複製並貼上 Visio 圖形"
  - "Visio [Visual Studio 中的 Office 程式開發]，複製並貼上 Visio 圖形"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：以程式設計方式在 Visio 文件中複製並貼上圖形
  您可以程式設計方式，將文件頁面上的圖形複製貼到同一份文件的另一個新頁面上。 您可以選擇將圖形貼到預設位置 \(使用中視窗的中央\)，或是貼到與原始頁面一樣的座標位置。  
  
## 複製並貼上圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) 和 [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835) 旗標的 VBA 參考文件。  
  
#### 若要將圖形複製至另一頁的中央  
  
-   下列範例會示範如何從第一個頁面複製圖形，並貼到第二個頁面的中央。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## 複製圖形並以相同位置貼上圖形  
 如需物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) 和 [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) 方法以及 [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835) 旗標的 VBA 參考文件。  
  
 如果需要控制貼上資訊的格式以及 \(選擇性\) 建立來源檔案 \(例如 Microsoft Office Word 文件\) 的連結，請使用 PasteSpecial 方法。  
  
#### 若要將圖形和圖形位置複製到另一頁  
  
-   下列範例會示範如何從第一個頁面複製圖形，並以其原始座標位置貼到第二個頁面。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)   
 [如何：以程式設計方式將圖形加入至 Visio 文件](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  