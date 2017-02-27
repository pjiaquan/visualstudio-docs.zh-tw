---
title: "使用舊版 API 存取文字圖層 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-文字圖層"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 使用舊版 API 存取文字圖層
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字層通常會封裝文字配置的某些特質。  在包含插入號 \(文字插入點\) 的函式前後，比方說，"函式\-一次 「 圖層隱藏的文字。  
  
 文字層之間的緩衝區，並在檢視中，並修改檢視表，會看到 「 緩衝區的內容的方式。  
  
## 文字層次資訊  
 下列清單說明文字的圖層的運作方式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]：  
  
-   語法標色和標記，可以裝飾文字層中的文字。  
  
-   目前無法實作您自己的圖層。  
  
-   圖層公開 \(expose\) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，其衍生自<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。  文字緩衝區本身也是當作圖層，這可讓檢視中，以處理以多型態基礎層級實作。  
  
-   任何數目的圖層可能位於檢視\] 和 \[緩衝區之間。  每個圖層只處理它下, 面的圖層，並檢視處理主要是出在最高的層級。  \(檢視並不會有一些資訊緩衝區\)。  
  
-   圖層會影響到其下的層級。  它不會影響上層超過來自標準事件。  
  
-   在 \[編輯器\] 中，隱藏的文字、 綜合文字和文字換行功能實作為層級。  您不需要直接互動的圖層可實作合成的隱藏文字。  如需詳細資訊，請參閱 [舊版語言服務中的大綱](../extensibility/internals/outlining-in-a-legacy-language-service.md)和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>。  
  
-   每個文字層都透過自己區域座標系統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>介面。  行換行的圖層，比方說，可能會包含兩行而基礎文字緩衝區可能包含單行。  
  
-   檢視會通訊至圖層上透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>介面。  您可以使用這個介面來調解緩衝區座標與檢視座標。  
  
-   任何層級化例如來源文字的合成文字層必須提供本機實作系統給<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>。  
  
-   除了<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，文字層必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>並引發事件，在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>介面。  
  
## 請參閱  
 [語法著色中自訂編輯器](../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [使用舊版 API 自訂編輯器控制項和功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)