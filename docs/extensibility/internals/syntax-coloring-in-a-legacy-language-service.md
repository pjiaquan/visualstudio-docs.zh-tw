---
title: "語法著色在舊版語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語法著色"
  - "語言服務語法標色"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 語法著色在舊版語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用色彩服務辨識的語言項目並將它們顯示在編輯器中指定的色彩。  
  
## Colorizer 模型  
 語言的服務實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面，將由編輯器。  這項實作是語言服務中，從另一個物件，如下列圖例所示。  
  
 ![SVC 色彩標示器圖形](~/docs/extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
簡單的 colorizer 模型  
  
> [!NOTE]
>  語法色彩服務是有別於一般[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colorizing 文字的機制。  如需有關一般[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] colorizing，所支援的機制，請參閱[使用字型和色彩](../../extensibility/using-fonts-and-colors.md)。  
  
 除了 colorizer，語言服務可以提供自訂的可設定色彩項目，由編輯器\] 中的廣告會提供自訂的可設定色彩項目。  您可以藉由實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>上相同的物件實作的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。  當編輯器\] 中的呼叫時，它會傳回自訂的可設定色彩項目數目<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，並傳回個別的自訂可設定色彩項目時，編輯器會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法會傳回物件實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。  如果語言服務支援 24 位元\] 或 \[高的色彩值，它必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>上相同的物件，做為介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。  
  
## VSPackage 如何使用語言服務 Colorizer  
  
1.  VSPackage 必須取得適當的語言服務，這需要語言服務來執行下列 VSPackage：  
  
    1.  使用物件實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面，以取得會以色彩標示的文字。  
  
         文字通常會顯示使用物件實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。  
  
    2.  取得語言服務的查詢語言服務 GUID VSPackage 的服務提供者。  語言服務會識別在登錄中，依檔案副檔名。  
  
    3.  將相關聯的語言卸除<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>點撥打的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法。  
  
2.  VSPackage 現在可以取得並使用 colorizer 物件，如下所示：  
  
    > [!NOTE]
    >  取得語言服務的 colorizer 物件明確不需要使用核心編輯器的 VSPackages。  核心編輯器的執行個體取得適當的語言服務，因為它會執行下面顯示的所有顏色標示任務。  
  
    1.  取得語言服務的 colorizer 物件會實作`T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`，以及<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>介面，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>上語言服務的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。  
  
    2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以取得特定範圍的 colorizer 資訊的文字。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>傳回一個用來以色彩標示的文字範圍中的每個字元的值陣列。  這些值會插入可設定色彩的項目清單是由核心編輯器所維護的預設值可設定色彩的項目清單或自訂的可設定色彩項目清單本身的語言服務所維護的索引。  
  
    3.  使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以顯示選取的文字。  
  
> [!NOTE]
>  除了使用語言服務 colorizer，VSPackage 也可以使用一般用途[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文字上色的機制。  如需有關這項機制的詳細資訊，請參閱[使用字型和色彩](../../extensibility/using-fonts-and-colors.md)。  
  
## 本章節內容  
 [實作語法標色](../../extensibility/internals/implementing-syntax-coloring.md)  
 討論語言服務的語法標色和語言服務必須以支援語法的實作色彩編輯器存取的方式。  
  
 [如何: 使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 示範如何使用內建的可設定色彩項目，從語言服務。  
  
 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)  
 討論如何實作自訂的可設定色彩項目。  
  
## 請參閱  
 [使用字型和色彩](../../extensibility/using-fonts-and-colors.md)