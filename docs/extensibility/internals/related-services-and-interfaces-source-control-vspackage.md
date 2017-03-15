---
title: "相關的服務及介面 (原始檔控制 VSPackage) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>相關的服務及介面 (原始檔控制 VSPackage)
此區段會列出所有的原始檔控制中的 VSPackage 相關介面[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。 原始檔控制 VSPackage 實作這些介面部分，並使用其他人來完成原始檔控制工作。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>實作和原始檔控制 VSPackages 介面  
 下列介面詳述於[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，和原始檔控制 VSPackage 實作它們的子集根據其所需的功能集。 某些介面標示為所需，而且必須實作的每個原始檔控制 VSPackage。  
  
 封裝不會實作，這些介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的預設實作。 請注意，預設實作針對沒有 VSPackage 已註冊的情況下並沒有任何專案被控制。 所有必要的介面，而不讓這些介面的預設實作，可實作適當撰寫的原始檔控制 VSPackage。  
  
 原始檔控制 VSPackage 必須實作的部分或所有下列介面會封裝的私用服務。  
  
 介面包括︰  
  
-   必要︰ 適當的實體 (原始檔控制 VSPackage，原始檔控制虛設常式，project) 必須實作介面。  
  
-   建議值︰ 實體應該實作這個介面。否則，您可能會限制原始檔控制功能。  
  
-   選擇性︰ 實體可以實作這個介面可提供更豐富的功能集。  
  
|介面|用途|由下列實作|實作？|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|編輯器呼叫這個介面之前修改或儲存檔案。 原始檔控制 VSPackage 可以簽出檔案，或拒絕此作業，如果簽出失敗。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|這個介面會提供基本的原始檔控制功能的專案，例如註冊和取消註冊與原始檔控制專案以及基本的原始檔控制圖像 （glyph） 提供支援。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|這個介面取自<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>使用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>函式，或只將轉型物件實作`IVsHierarchy`到`IVsSccProject2`。</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 它用於在專案中的原始檔控制下檔案或通知目前的原始檔控制狀態或位置的專案。|專案|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|整合模組會使用此介面來設定目前使用中的 VSPackage。|原始檔控制 VSPackage|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|這個介面根據訂閱模型。 任何 VSPackage 可以發出信號它要接收的文件的事件通知的殼層即將發生的事件。 它是實作，並由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，依序傳遞事件實作`IVsTrackProjectDocumentsEvents2`到 VSPackage。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|這個介面會提供批次的處理、 同步處理的讀取/寫入作業，以及進階`OnQueryAddFiles`方法。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**方案總管 中**和新的檔案會新增至專案，或重新命名或從專案刪除檔案和資料夾時，專案會呼叫這個介面。 原始檔控制 VSPackage 可以簽出專案檔，或取消作業。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**方案總管 中**專案呼叫這個介面，以回應 IVstrackProjectDocuments3 介面方法的呼叫。 VSPackage 可以追蹤同步處理的批次的作業的原始檔控制讀取/寫入作業，並使用更多進階`OnQueryAddFiles`方法。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|這個介面提供登錄的管理支援 Web 專案。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|這個介面用來擷取專案中的原始檔控制檔案的工具提示。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|這個介面提供延伸模組支援的命名空間。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage 整合到命名空間擴充功能會使用此介面**新增**，**開啟**，或**儲存**對話方塊。 因此，專案可以自動新增至原始檔控制，在建立，或加入時儲存的原始檔控制作業就會生效。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage 會使用此介面，以定義其他的圖像 （glyph） 節點中的來源控制圖像**方案總管 中**。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**新增**Web 專案 對話方塊會使用此介面。 它提供方法來瀏覽原始檔控制位置和開啟 Web 專案之前新增至該位置的原始檔控制儲存機制。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|這個介面會提供非同步 （背景） 載入，從原始檔控制專案的支援。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|這個介面可讓專案，以查看由<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>起始非同步載入的進度|專案|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|這個介面可讓查詢使用中的原始檔控制 VSPackage IDE。 IDE 會查詢甚至不會有作用中來源控制 VSPackage 註冊時，才有意義的原始檔控制設定的值。 這個介面會實作，並由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|原始檔控制虛設常式|必要|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|此介面用於註冊的原始檔控制 VSPackage。|原始檔控制虛設常式|必要|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|這個介面用於自動化。 因此，它會公開可執行而不顯示任何 UI 函式。|原始檔控制 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|這個介面用來儲存方案 (.sln) 檔案中原始檔控制設定。 設定包括原始檔控制位置和原始檔控制狀態旗標。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|這個介面用來儲存方案的選項 (.suo) 檔案中的原始檔控制設定。 這可能包括使用者特定的原始檔控制設定，例如目前使用者的登錄位置。|原始檔控制 VSPackage|建議|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|這個介面用來監視事件，以執行作業，例如簽入之前關閉方案，或開啟專案時，取得新的檔案從原始檔控制的專案檔案。|原始檔控制 VSPackage|建議|  
  
## <a name="see-also"></a>另請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
