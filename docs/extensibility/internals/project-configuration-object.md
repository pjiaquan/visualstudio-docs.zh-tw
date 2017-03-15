---
title: "專案組態物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
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
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>專案組態物件
專案組態物件管理 ui 的組態資訊的顯示。  
  
 ![Visual Studio 專案組態](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
專案組態屬性頁  
  
 專案組態提供者管理專案組態。 環境和其他封裝，來存取和擷取有關專案組態的資訊，請呼叫附加至專案的組態提供者物件的介面。  
  
> [!NOTE]
>  您無法建立或編輯的方案組態檔，以程式設計的方式。 您必須使用`DTE.SolutionBuilder`。 請參閱[方案組態](../../extensibility/internals/solution-configuration.md)如需詳細資訊。  
  
 若要發行可用於組態 UI 中的顯示名稱，您的專案應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，它會傳回一份`IVsCfg`可用來取得環境的 UI 中列出的組態與平台資訊的顯示名稱的指標。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> 使用中的組態與平台是由儲存在作用中方案組態中的專案的設定決定。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可以用來擷取使用中的專案組態。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>物件可以選擇性地實作上<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>物件可讓您擷取`IVsProjectCfg2`物件會根據標準的專案組態名稱。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>  
  
 提供存取權的專案組態的環境和其他專案的另一個方法是讓專案提供的實作`IVsCfgProvider2::GetCfgs`方法來傳回一個或多個組態物件。 專案可能也會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，繼承自`IVsProjectCfg`，藉此從`IVsCfg`，以提供特定組態資訊。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>新增、 刪除和重新命名專案組態的支援平台和功能。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  由於 Visual Studio 不再限於兩種組態類型，撰寫程式碼處理組態應該不會假設大約數目的設定，也不應該它寫入的假設有一個組態的專案，則需要偵錯或其他。 這可讓使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>過時。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>  
  
 呼叫`QueryInterface`從傳回的物件上`IVsGetCfgProvider::GetCfgProvider`擷取`IVsCfgProvider2`。 如果`IVsGetCfgProvider`藉由呼叫找不到`QueryInterface`上`IVsProject3`專案物件，您可以存取的組態提供者物件呼叫`QueryInterface`階層根瀏覽器物件傳回的物件上`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`，或透過組態提供者傳回的指標`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`。  
  
 `IVsProjectCfg2`主要是提供存取建置、 偵錯和部署管理物件，並讓專案輸出群組的自由。 方法的`IVsProjectCfg`和`IVsProjectCfg2`可以用來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>管理建置程序和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>組態的輸出群組的指標。</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>  
  
 專案必須傳回相同數目的群組，即使群組內包含的輸出數目而異的組態設定，它支援每個組態。 群組必須也有相同的識別元資訊 （正式名稱、 顯示名稱和群組資訊） 組態設定專案中。 如需詳細資訊，請參閱[輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
 若要啟用偵錯，您的設定應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`是選擇性的介面實作的偵錯工具啟動組態的專案，並與組態物件上實作`IVsCfg`和`IVsProjectCfg`。 在使用者選擇按下 F5 開始偵錯工具時，環境會呼叫它。  
  
 `ISpecifyPropertyPages`和`IDispatch`屬性頁的搭配使用來擷取並向使用者顯示組態相關資訊。 如需詳細資訊，請參閱[屬性頁](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案建置組態](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)   
 [屬性頁](../../extensibility/internals/property-pages.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)
