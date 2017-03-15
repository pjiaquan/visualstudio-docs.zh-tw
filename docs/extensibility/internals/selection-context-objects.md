---
title: "選擇內容物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
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
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>選擇內容物件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 來判斷應該顯示在 IDE 中使用全域選擇內容物件。 每個視窗在 IDE 中的可以有自己推送至全域範圍內容的選取項目內容物件。 該視窗具有焦點時，IDE 會更新全域範圍內容視窗中的值。 如需詳細資訊，請參閱[給使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)。  
  
 每個視窗框架或在 IDE 中的站台有一個稱為<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服務 設置在視窗框架的 VSPackage 所建立的物件必須呼叫`QueryService`方法來取得變數的指標，<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 框架視窗可以保持傳播至全域範圍內容時便會啟動其選取項目內容資訊的部分。 這項功能可用於工具視窗，可能必須重新啟動與空的選取項目。  
  
 修改 VSPackages 可以監視全域選擇內容觸發程序事件。 VSPackages 可以執行下列工作，藉由實作`IVsTrackSelectionEx`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>介面︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   更新階層中目前使用中的檔案。  
  
-   監視變更為特定類型的項目。 例如，如果 VSPackage 使用特殊**屬性** 視窗中，您可以監視使用中的變更**屬性**視窗，您需要時重新啟動。  
  
 下列程序會顯示選取項目追蹤的一般程序。  
  
1.  IDE 會從新開啟的視窗擷取選取項目內容，並將它放在全域範圍內容。 如果選取範圍內容使用 HIERARCHY_DONTPROPAGATE 或 SELCONTAINER_DONTPROPAGATE，該資訊不會傳播到全域內容。 如需詳細資訊，請參閱[給使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)。  
  
2.  通知事件會廣播至任何要求它們的 VSPackage。  
  
3.  VSPackage 處理程式碼執行活動，例如更新階層中，重新啟動一項工具或其他類似工作的方式接收的事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [選取項目和 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [專案類型](../../extensibility/internals/project-types.md)
