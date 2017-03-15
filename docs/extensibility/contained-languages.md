---
title: "包含的語言 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-包含語言"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 包含的語言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*包含語言*都是包含其他語言的語言。  例如，HTML [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]分頁也可能含有[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]指令碼。  雙重語言架構都需要.aspx 檔案編輯器中以 HTML 和指令碼語言都提供 IntelliSense、 顏色及其他編輯功能。  
  
## 實作  
 最重要的介面，您必須實作所包含的語言是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。  沒有裝載於主要語言的語言會實作這個介面。  它讓存取語言服務的 colorizer 文字檢視，其主要語言服務 id。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>可讓您建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。  下列步驟將告訴您，如何實作所包含的語言：  
  
1.  使用`QueryService()`以取得語言服務識別碼和介面 ID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>方法，以建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>介面。  傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面，項目 ID \(一個或多個<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>， <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>，或<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) 和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面。  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>介面，也就是文字緩衝區協調器物件，提供基本的服務，才能對應到第二個語言的緩衝區在主要檔案的位置。  
  
     例如，在單一.aspx 檔案中，主要檔案包含 ASP、 HTML 和所包含的所有程式碼。  不過，第二個緩衝區，包括只是內含的程式碼，加上任何類別定義，讓次要緩衝區有效的程式碼檔。  緩衝區的協調者會處理協調到另一個緩衝區中的編輯工作。  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>方法，這是主要的語言，告訴緩衝區協調者的緩衝區內的文字內容對應至次要緩衝區中相對應的文字。  
  
     陣列中的語言會傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping>結構，且目前只包括主要和次要的範圍。  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>方法，並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>方法提供的對應，從主要至次要緩衝區，反之亦然。