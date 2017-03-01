---
title: "自訂使用者介面 (原始檔控制 VSPackage) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>自訂使用者介面 (原始檔控制 VSPackage)
VSPackage 透過 Visual Studio 命令資料表 (.vsct) 檔案中宣告它的功能表項目和其預設狀態。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會顯示在其預設狀態中的功能表項目直到載入 VSPackage。 接著，<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>會呼叫方法來啟用或停用功能表項目。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 讓 VSPackage 可以根據命令使用者介面 (UI) 內容自動載入 VSPackage 可以設定登錄機碼，而非只切換到特定的 UI 內容視雖然原始檔控制通常應該載入 VSPackage。 如需 AutoLoadPackages 登錄機碼的詳細資訊，請參閱[管理 VSPackages](../../extensibility/managing-vspackages.md)。  
  
## <a name="vspackage-ui"></a>VSPackage UI  
 原始檔控制套件會實作為 VSPackage，而不使用任何 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每個原始檔控制 VSPackage 必須指定它自己的 UI 項目，例如功能表項目、 功能表群組、 工具視窗、 工具列和任何必要的 UI 設定原始檔控制 VSPackage 的特定選項。 靜態或動態方式，您可以啟用這些 UI 項目。 靜態的 UI 項目.vsct 檔中定義，並顯示是否或未載入 VSPackage。 動態 UI 元素，例如可能會顯示特定命令 UI 內容中，根據<xref:EnvDTE.Constants.vsContextNoSolution>，或做為呼叫的結果<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> 延遲載入 Vspackage 的策略符合動態 UI 項目的可見性。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>原始檔控制 VSPackages UI 條件約束  
 原始檔控制 VSPackage 無法移除從 IDE 會在載入之後，因為 VSPackage 必須能夠進入非作用中狀態。 當 VSPackage 收到通知，就無法再使用中時，VSPackage 停用其 UI，並忽略任何外部的 IDE 互動。 VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法應該隱藏命令的 VSPackage 為非現用時。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 VSPackage 必須實作每個原始檔控制`IVsSccProvider`介面。 在介面中，兩個方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>，必須實作 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 原始檔控制各種所實作的 IDE 事件可能已訂閱 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>， <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>，依此類推。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 此外，VSPackage 可能未實作登錄啟用回呼介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 這些必須全部忽略非使用中時。  
  
 下列清單顯示受影響的原始檔控制 VSPackage 的作用中狀態的介面︰  
  
-   追蹤專案文件的事件。  
  
-   方案的事件。  
  
-   解決方案的持續性介面。 當非作用中時，封裝應寫入.sln 和.suo 檔案。  
  
-   屬性擴充項。  
  
 必要<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>，並也與原始檔控制相關聯的任何選擇性介面不會呼叫非作用中的原始檔控制 VSPackage 時。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 啟動時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令 UI 內容設定為目前的預設原始檔控制 VSPackage 識別碼的識別碼 這會導致靜態 UI 的使用中的原始檔控制出現在 IDE 中，而不用實際載入 VSPackage 的 VSPackage。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]暫停向 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>得 VSPackage 的任何呼叫之前。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 下表描述的特定詳細資料，需有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 會隱藏不同的 UI 項目。  
  
|UI 項目|描述|  
|-------------|-----------------|  
|功能表與工具列|原始檔控制套件必須設定初始功能表和工具列的可見性狀態中的原始檔控制封裝識別碼[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct 檔的區段。 這可讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 來正確設定功能表項目的狀態，而不需要載入 VSPackage 和呼叫的實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|工具視窗|原始檔控制 VSPackage 會隱藏非作用中時，就會擁有任何工具視窗。|  
|原始檔控制 VSPackage 特定選項頁|登錄機碼 HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts 可讓您設定的內容中需要顯示其選項頁面的 VSPackage。 此機碼下的登錄項目，就必須使用服務識別碼 (SID) 的原始檔控制服務，並將它指派 1 的 DWORD 值，來建立。 UI 事件發生時的內容中會向 VSPackage 的原始檔控制，如果使用中，則會呼叫 VSPackage。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)
