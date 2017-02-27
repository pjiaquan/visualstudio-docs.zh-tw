---
title: "視覺化檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, 視覺化檢視"
  - "視覺化檢視"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# 視覺化檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

視覺化檢視是 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具使用者介面的元件。  「*視覺化檢視*」\(Visualizer\) 會建立對話方塊或其他介面，以適用於其資料類型的方式來顯示變數或物件。  例如，HTML 視覺化檢視會解譯 HTML 字串，並在瀏覽視窗中顯示出現的結果，而點陣圖視覺化檢視會解譯點陣圖結構，並顯示其所代表的圖形。  除了檢視資料外，有些視覺化檢視也能讓您修改資料。  
  
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具包含六個標準視覺化檢視。  它們分別為文字、HTML、XML 及 JSON 視覺化檢視、WPF 樹狀架構視覺化檢視和資料集視覺化檢視。前三者適用於字串物件，WPF 樹狀架構視化檢視可用來顯示 WPF 物件視覺化樹狀結構，而資料集視覺化檢視則適用於資料集、DataView 和 DataTable 物件。  額外的視覺化檢視未來可能可以從 Microsoft Corporation 下載，且可從協力廠商和社群取得。  此外，您可以自行撰寫視覺化檢視，並將它們安裝至 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 偵錯工具中。  
  
> [!NOTE]
>  在**市集**應用程式中，只支援標準文字、HTML、XML 及 JSON 視覺化檢視。  不支援自訂 \(使用者建立的\) 視覺化檢視。  
  
 偵錯工具中的視覺化檢視是以放大鏡圖示表示。  當您在 \[**DataTip**\]、\[偵錯工具變數\] 視窗或 \[**快速監看式**\] 對話方塊中看見放大鏡時，可以按一下放大鏡，選擇適合對應物件資料類型的視覺化檢視。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
>  偵錯工具視覺化檢視需要比部分信任應用程式所允許還要大的權限。  因此，當您在部分信任的程式碼中被停止時，視覺化檢視將不會載入。  若要使用視覺化檢視進行偵錯，您必須以完全信任方式執行程式碼。  
  
## 在本節中  
 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)  
  
 [逐步解說：在 C\# 中撰寫視覺化檢視](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)  
  
 [如何：測試和偵錯視覺化檢視](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)  
  
 [視覺化檢視 API 參考](../debugger/visualizer-api-reference.md)  
  
## 相關章節  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)