---
title: "提供概述支援的語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何︰ 展開大綱中提供支援舊版語言服務
有兩個選項，來擴充您的語言支援的大綱支援**摺疊至定義**命令。 您可以新增編輯器控制大綱區域，以及新增用戶端控制大綱區域。  
  
## <a name="adding-editor-controlled-outline-regions"></a>加入編輯器控制大綱區域  
 使用這種方法來建立大綱區域，然後讓處理是否展開區域時，編輯器摺疊，等等。 此選項提供大綱支援兩個選項，是最不穩固。 此選項時，您必須建立新的大綱區域上指定的一段文字使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 此區域建立之後，其行為會受到編輯器 中。 您可以使用下列程序來實作編輯器控制大綱區域。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>若要實作一個編輯器控制大綱區域  
  
1.  呼叫`QueryService`的<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     這讓指標回到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，並傳入指定的文字緩衝區的指標。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 這會傳回指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件緩衝區。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>指標</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>上</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>呼叫  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>加入一個或多新增一次大綱區域。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     這個方法可讓您指定的大綱、 移除或保留現有的大綱區域是否和大綱區域是否為展開或摺疊的預設值的文字範圍。  
  
## <a name="adding-client-controlled-outline-regions"></a>新增用戶端控制大綱區域  
 使用這個方法來實作，用戶端控制 （或智慧型） 大綱喜歡使用[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]語言服務。 語言服務，可管理自己的大綱監視文字緩衝區內容，以摧毀舊的大綱區域，他們就會變成無效時，並視需要建立新的大綱區域。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>若要實作的用戶端控制大綱區域  
  
1.  呼叫`QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 這讓指標回到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，並傳入指定的文字緩衝區的指標。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 這會決定是否隱藏的文字工作階段已經存在的緩衝區。  
  
3.  如果文字工作階段已經存在，則不需要建立一個，並指向現有的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 使用此指標來列舉並建立大綱區域。 否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>建立隱藏的文字工作階段的緩衝區。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>，您可以指定隱藏的文字，用戶端 (也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>物件)。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 此用戶端通知時隱藏文字，或是展開或摺疊，只要使用者大綱區域。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>結構) 參數︰ 指定的值為<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>中`iType`成員<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您要建立一個大綱區域，而不是隱藏的區域。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 指定的區域是用戶端控制，或在編輯器控制`dwBehavior`成員<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 智慧型的大綱實作可以包含混合的編輯器和用戶端控制大綱區域。 指定大綱區域摺疊時，例如"..."，在顯示的橫幅文字`pszBanner`成員<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 編輯器的隱藏區域的預設橫幅文字是"..."。
