---
title: "如何︰ 支援舊版語言服務中的大綱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，摺疊至定義命令"
  - "語言服務，支援摺疊至定義命令"
  - "隱藏的文字，摺疊至定義命令"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何︰ 支援舊版語言服務中的大綱
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大綱用來展開或摺疊的文字不同的區域。 使用方式大綱定義不同的語言不同。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作大綱的新方法的詳細資訊，請參閱 [逐步解說: 大綱](../../extensibility/walkthrough-outlining.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 下列示範如何支援這個命令語言服務。  
  
### 若要支援大綱  
  
1.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> 語言服務物件上。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 目前大綱工作階段物件，將新的大綱區域上。  
  
## 穩固程式設計  
 當使用者選取 **摺疊至定義** 上 **大綱** \] 功能表上，IDE 會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 您語言的服務。  
  
 呼叫這個方法時，IDE 會將中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 指標 （文字緩衝區的指標） 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> （目前的大綱工作階段的指標）。  
  
 您可以呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 方法來指定這些區域中的多個大綱區域 `rgOutlnReg` 參數。`rgOutlnReg` 參數是 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 結構。 此程序可讓您指定不同的隱藏區域，例如是否在特定區域會展開或摺疊的特性。  
  
> [!NOTE]
>  請務必小心有關隱藏新行字元。 隱藏的文字應該擴充從第一行的開始到最後一個字元的最後一行的區段中，只顯示最終的新行字元。  
  
## 請參閱  
 [如何︰ 隱藏的文字中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [如何︰ 展開大綱中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)