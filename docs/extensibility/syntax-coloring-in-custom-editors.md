---
title: "語法著色中自訂編輯器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，自訂的語法標色"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 語法著色中自訂編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 環境 SDK 編輯器，包括核心編輯器\] 中，會使用語言服務，來識別特定的語法項目，並使用指定的文件檢視的指定色彩顯示。  
  
## 顏色標示需求  
 所有編輯器實作語言服務的 colorizer 都必須：  
  
1.  使用物件實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>來管理以色彩標示的文字和物件實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>提供文件檢視的文字。  
  
2.  查詢使用語言服務的識別 GUID 的 VSPackage 服務提供者，以取得特定語言服務的介面。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>的物件實作的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。  這個方法將相關聯的語言卸除<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage 用來管理要能以色彩標示文字的實作。  
  
## 核心編輯器的語言服務的 Colorizer 的使用方式  
 Colorizer 的語言服務時，核心編輯器、 剖析和轉譯的文字語言服務的 colorizer 的執行個體來取得自動發生而不需要您採取任何進一步的介入。  
  
 IDE 以透明方式：  
  
-   呼叫地剖析和分析文字，因為它是在新增或修改的實作 colorizer 視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。  
  
-   確保所提供的文件檢視所提供的顯示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>實作更新，並重新繪製使用 colorizer 所傳回的資訊。  
  
## 語言服務的 Colorizer 的非核心編輯器使用方式  
 非核心編輯器執行個體也可以使用語言的語法顏色標示服務，但是它們必須明確地擷取和套用服務的 colorizer 和重繪其本身的文件檢視模式。  
  
 若要執行這項操作需要非核心編輯器：  
  
1.  取得語言服務的 colorizer 物件 \(哪一個實作`T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\)。  您 VSPackage 的運作方式是呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>語言服務的介面上的方法。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以要求特定的文字範圍會以色彩標示。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法會傳回一個陣列值、 另一個則用於在文字中的每個字母跨越以色彩標示。  它也可識別特定類型的可設定色彩的項目，例如註解、 關鍵字或資料型別為文字範圍。  
  
3.  使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>重繪，並顯示其文字。  
  
> [!NOTE]
>  除了使用語言服務的 colorizer，VSPackage 可以選擇要使用的一般用途的 Visual Studio 環境 SDK 文字上色機制。  如需有關這項機制的詳細資訊，請參閱[使用字型和色彩](../extensibility/using-fonts-and-colors.md)。  
  
## 請參閱  
 [語法著色在舊版語言服務](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法標色](../extensibility/internals/implementing-syntax-coloring.md)   
 [如何: 使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自訂色彩的項目](../extensibility/internals/custom-colorable-items.md)