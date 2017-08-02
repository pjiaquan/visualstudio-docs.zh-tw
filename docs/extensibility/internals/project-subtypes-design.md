---
title: "專案的子型別設計 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案的子類型設計"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# 專案的子型別設計
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案子類型可讓 VSPackages 延伸 Microsoft 建置引擎 \(MSBuild\) 為基礎的專案。  使用彙總可以讓您重複使用大部分受管理的核心專案系統中實作的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]卻仍然來自訂特定案例的行為。  
  
 下列主題詳細說明基本的設計與實作專案子類型：  
  
-   專案子類型的設計。  
  
-   多層級的彙總。  
  
-   支援的介面。  
  
## 專案子型別設計  
 專案子類型的初始設定，來彙總主達成<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>物件。  此彙總可以讓您覆寫或增強的基底的專案功能的大部分專案子類型。  專案子類型取得初次出現的處理屬性使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>，命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>，並使用的專案項目管理<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>。  此外，也可以擴充專案子類型：  
  
-   專案組態的物件。  
  
-   組態相關的物件。  
  
-   瀏覽\] 組態無關的物件。  
  
-   專案的自動化物件。  
  
-   專案自動化屬性集合。  
  
 如需有關的專案子類型的擴充性的詳細資訊，請參閱[屬性和方法的擴充專案子類型](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。  
  
##### 原則檔  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境提供的擴充基底的專案系統在原則檔實作專案子類型與範例。  原則檔允許的外形[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境，藉由管理功能，包括 \[方案總管\] 中， **加入專案**對話方塊中， **加入新項目** 對話方塊中，並**屬性**對話方塊。  覆寫原則子型別，並增強了這些功能，透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>， `IOleCommandTarget`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>的實作。  
  
##### 彙總機制  
 環境的專案子類型彙總機制可支援多個層級的彙總，因此可允許進階實作來進一步 flavoring flavored 的專案的子型別。  子也支援專案的物件類型，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>，設計用來允許多個層級的分層。  為了與 COM 與 COM 的條件約束彙總規則、 專案的子型別和基底的專案必須相互合作地進行程式設計，讓內部的子型別或基底的專案，以適當地加入委派方法呼叫，和管理參考計數。  也就是要被聚合的專案必須設計用來支持集合。  
  
 下圖顯示多層級專案子類型彙總示意表示的法。  
  
 ![Visual Studio 多層 projectflavor 圖形](~/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
多層次的專案子類型  
  
 多層級專案的子型別集合是由三個層級，基底的專案，這是依專案的子型別，那麼進一步彙總的進階的專案子類型所組成。  圖的重點在於某些支援的介面所提供的一部份[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案子類型的架構。  
  
##### 部署機制  
 基底的專案系統的許多功能增強專案子類型，包括部署機制。  專案子類型會影響所實作的介面設定的部署機制 \(例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\)，藉由呼叫 QueryInterface 上擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>。  在此案例中的專案子類型\] 與 \[進階的專案子類型加入不同的設定的實作，基底的專案會呼叫`QueryInterface`上的進階的專案子類型`IUnknown`。  如果內嵌專案子類型，包含組態實作的基底的專案，進階的專案子類型是委派實作所提供的內嵌專案子類型。  若要保存從一個彙總層級的狀態到另一種機制，以實作專案子類型的所有層級<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>來保存非建置到專案檔相關的 XML 資料。  如需詳細資訊，請參閱 [在 MSBuild 專案檔案中保存的資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。  <xref:EnvDTE80.IInternalExtenderProvider>會實作為一種機制，若要自動化的擴充項擷取專案子類型。  
  
 下圖著重在自動化的擴充項實作中，瀏覽專案組態的物件特別的是，用來擴充基底的專案系統專案子類型。  
  
 ![VS 專案類別自動擴充項圖形](~/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
專案子類型自動化擴充項。  
  
 專案子類型可以擴充自動化物件模型，進一步擴充基底的專案系統。  這些無誤 DTE automation 物件的一部份，且用來擴充 \[專案\] 物件中， `ProjectItem`物件，並`Configuration`物件。  如需詳細資訊，請參閱 [擴充基底專案物件的模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。  
  
## 多層級的彙總  
 包裝較低的層級專案子類型的專案子型別實作必須相互合作地設計以允許內嵌專案子類型，才能正確執行。  一份程式設計責任包括：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>包裝內部的子類型的專案子類型的實作必須委派給<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>內嵌專案的子型別實作兩個<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法。  
  
-   <xref:EnvDTE80.IInternalExtenderProvider>的包裝函式專案子型別實作必須委派，其內部的專案子類型。  特別是實作<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>需要從內嵌專案的子型別中取得之名稱的字串，然後將它想要加入做為擴充項的字串連接起來。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>的包裝函式專案子型別實作必須具現化<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>物件，其內部的專案子類型，而且保留為私用的委派，因為只有基底專案的專案組態物件直接知道包裝函式專案子類型的組態物件是否存在。  外部專案的子型別可以一開始選擇要直接處理設定介面，並再委派至內嵌專案子類型實作其他<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>。  
  
## 支援的介面  
 基底的專案就是委派呼叫支援介面加入專案的子型別，以擴充它的實作的各種層面。  這包括擴充專案組態的物件和屬性瀏覽器的不同物件。  這些介面會擷取藉由呼叫`QueryInterface`上`punkOuter` \(變數的指標， `IUnknown`\) 的最外層的專案子類型彙總工具。  
  
|介面|專案子類型|  
|--------|-----------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|可讓專案的子型別為：<br /><br /> -   提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 的實作。<br />-   藉由使用專案子類型，以提供自己的實作的控制在偵錯工具中的啟動<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。<br />-   停用設計階段運算式評估，適當地處理`DBGLAUNCH_DesignTimeExprEval`在實作案例<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|可讓專案的子型別為：<br /><br /> -   擴充<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>要新增或移除設定獨立專案的屬性中的專案。<br />-   擴充專案 automation 物件 \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) 的專案。<br /><br /> 上述的屬性值取自<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列舉型別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|可讓專案的子型別對應至<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>給定專案組態瀏覽的物件的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|可讓專案的子型別對應至<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>或`VSITEMID`物件，指定專案設定瀏覽的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|可讓專案的子型別來保存專案檔 \(.vbproj 或.csproj\) 的任意結構化的 XML 資料。  這項資料是看不到 MSBuild。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|可讓專案的子型別為：<br /><br /> -   加入新的 MSBuild 屬性，可保存。<br />-   從 MSBuild 移除不必要的屬性。<br />-   目前的值，MSBuild 屬性的查詢。<br />-   變更目前的 MSBuild 屬性值。|  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>