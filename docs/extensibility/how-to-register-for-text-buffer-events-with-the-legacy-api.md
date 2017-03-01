---
title: "如何︰ 文字緩衝區使用註冊事件舊版 API |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>如何︰ 使用舊版 API 文字緩衝區事件註冊
如果您要使用舊版的 API 來存取文字緩衝區，您應該註冊文字緩衝區事件，如下列程序中所示。  
  
### <a name="to-advise-text-buffer-events"></a>若要通知檢索緩衝區事件  
  
1.  從上介面的其中一個指標<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>，呼叫`QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>指標</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>方法，並傳入要註冊的事件的介面 ID。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     例如，如果您想要註冊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>，然後傳入的介面 ID 的 IID_IVsTextLinesEvents。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     文字緩衝區的指標會傳回<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適當的連線點物件的介面。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  使用這個指標，呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>方法，傳遞至您的實作，您想要註冊，比方說，事件介面的指標`IVsTextLinesEvents`介面。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     在環境中傳回的 cookie，您可以在停止聽候事件，藉由呼叫使用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>另請參閱  
 [在舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)
