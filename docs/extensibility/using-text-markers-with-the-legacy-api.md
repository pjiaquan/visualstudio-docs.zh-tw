---
title: "使用舊版 API 中的文字標記 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，傳統的文字標記"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用舊版 API 中的文字標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字標記是文字的浮動在緩衝區中可能會影響到顯示範圍和文字區域的行為。  標記包括中斷點、 書籤、 波浪底線，以及唯讀區域。  文字標記是與語法標色基本上不同項目。  語法標色是文字的通訊區域相關聯的語言語法的快速方法。  當 Windows 在速度是很重要時，會重新繪製\] 畫面中，通常要求語法標色。  語法標色會變更文字的色彩。  文字標記可以變更許多其他的文字內容。  可以 「 浮動 」 文字的標記，並將其套用特殊的行為和色彩。  
  
 有鑑於此，效能的標記文字，等等相關聯的額外負荷不會建立許多文字緩衝區的標記。  每一個標記會更新每次使用者編輯緩衝區的內容。  
  
> [!NOTE]
>  使用者可以變更的 \[看得見的標記類型，但其圖案和樣式無法使用的色彩。  如需詳細資訊，請參閱 [選項對話方塊、環境、字型和色彩](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)|說明如何加入標準的文字資料標記的型別，所提供的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器到文字檢視。|  
|[How to: 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)|描述如何實作的執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用來藉由使用紅色波浪底線指出錯誤的標記。|  
|[如何: 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)|說明如何建立並將自訂文字的標記類型新增到文字檢視。|  
|[如何: 使用文字標記](../extensibility/how-to-use-text-markers.md)|說明如何新增文字的標記。|  
|[核心編輯器內](../extensibility/inside-the-core-editor.md)|說明核心編輯器的功能，並提供有關如何自訂核心編輯器的詳細資料。|  
|[Editor Features](http://msdn.microsoft.com/zh-tw/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|描述 \[可用功能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器。|  
  
## 參考資料  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 提供統一的機制，取得指定的文字標記型別相關資訊，無論是預先定義的編輯器\] 中，或由 VSPackage 登錄。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 提供存取權並調整文字緩衝區中的文字標記位置使用二維座標。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 提供方法來管理文字標記。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 提供回呼[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 和其他處理序用來調整文字的標記。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 擴充功能，可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 擴充功能，可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 啟用的標記類型，以判斷是否有其他標記型別共用相同的色彩設定。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 提供核心編輯器中的文字資料標記的內容。  每種核心編輯器中的文字標記類型，IDE 便會建立不同的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>物件。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 所提供的圖像 \(glyph\) 支援拖放編輯的標記處理常式。  圖像 \(glyph\) 是一個圖示，表示標記的位置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> ，提供給其他 VSPackages 的資料標記的文字服務的介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 提供存取權並調整文字緩衝區中的文字標記位置使用一維的座標。  如果可能的話，請勿使用這個介面。