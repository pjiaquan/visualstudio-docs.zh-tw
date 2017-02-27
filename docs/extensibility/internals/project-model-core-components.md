---
title: "專案模型的核心元件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案模型、 物件與介面"
  - "專案模型中服務"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 專案模型的核心元件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下表詳述的專案模型。  資料表顯示的介面和服務在模型中的介面和特定的物件相關聯的服務中所識別的簡短描述。  此外，資料表將詳細說明其他都是在專案建立和維護您的特定專案類型的需求而定選擇性的介面。  
  
 如需詳細資訊，請參閱 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
### 封裝物件  
  
|介面|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化在 IDE 中的 VSPackage 並將它的服務提供對 IDE。|  
  
### 專案工廠物件  
  
|介面|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|建立新的專案並開啟現有專案管理。|  
  
### 專案的物件  
  
|介面|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理加入和移除專案項目、 開啟編輯器，並會維護每個文件 moniker 之間的對應和`VSITEMID`。  繼承自`IVsProject`和`IVsProject2`。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理 \[巡覽\] 和 \[顯示\] 屬性，並提供的事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|啟用指令執行類似的`IOleCommandTarget`如剪下\] 和 \[重新命名套用只有當焦點位於方案總管\] 中的命令。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|當做專案階層架構的主要命令目標介面。  這是標準的介面來查詢它們的命令狀態\] 或 \[狀態\] 和 \[執行\] 命令的物件。  當您沒有焦點放在 \[專案\] 視窗中可以使用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調專案狀態的保存性。  一般而言，專案的狀態儲存為專案檔案，但可以適用於不是以檔案為基礎的存放系統。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|可讓專案管理其專案項目，以磁碟或其他存放裝置系統中的物件上的檔案的保存性的所有層面。  `IVsPeristHierarchyItem2`介面用於項目不會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調與原始程式碼控制互動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|可讓專案管理的組態資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案組態的物件，例如偵錯\/發行組態。  建置、 部署和偵錯作業會透過專案組態的物件一致。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|實作階層來控制刪除 \(刪除\)，或移除階層架構的項目 \(非破壞性\) 的選項。  呼叫查詢介面上`IVsHierarchyDeleteHandler`介面從`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供實作可以讓物件可支援`IVsCfgProvider2`上不同的 COM 識別專案物件和實作介面`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|若要讓您專案的 「 可延伸實作由其他開發人員的選擇性介面。  `IVsProjectStartupServices`介面可以讓要註冊您保存到專案檔案，以便每次您的專案載入時，您會載入協力廠商服務 GUID 到您的專案檔和呼叫的 GUID 的協力廠商 VSPackage `QueryService`的 GUID。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|由來源的階層架構中實作`UIHierarchy`協調剪貼簿\] 作業，例如剪下\]、 \[複製\]，並貼上的視窗。  使用`AdviseClipboardHelperEvents`登錄剪貼簿事件的介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供在 UI 階層視窗中拖放作業期間拖曳的項目，相對於其資料來源的相關資訊。  從呼叫`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供在 UI 階層視窗中拖放作業期間拖曳的項目，相對於其置放目標的相關資訊。  從呼叫`IVsHierarchy`介面。|  
  
### Configuration 物件  
  
|介面|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供設定的相關資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|可讓專案管理的組態資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|可讓偵錯工具控制下執行的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|實作執行其他專案的部署作業的部署專案。|  
  
### 設定產生器物件  
  
|介面|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案組態的建置作業。|  
  
### 其他專案的物件  
  
|介面|註解|  
|--------|--------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|顯示項目中的屬性**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示部署的輸出。|  
  
 下表顯示專案模型中所識別的服務的簡短描述。  
  
### 服務  
  
|服務|註解|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|由其專案工廠有 IDE 實作專案型別註冊的 VSPackages。  必須呼叫您的 VSPackage `QueryService` ，此服務，並登錄它的專案時`IVsPackage::SetSite`就會呼叫方法。  如果`SetSite`不會呼叫方法，您的專案不具現化。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供在 IDE 內部、 內建概念，目前的方案，例如列舉專案、 建立新的專案、 專案的變更，好等等的能力的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|呼叫被想要加入原始檔控制的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|維持開啟的文件，以判斷是否有一個以上的專案項目都已開啟的資料表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含介面和方法呼叫，以實際開啟專案項目使用標準編輯器\] 或 \[特定的編輯器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|必要時所要呼叫的所有專案也可以新增、 移除或重新命名其項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理檔案或目錄的變更並告知用戶端，當磁碟上已選取的檔案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|需要它們骯髒的項目，或將它們儲存之前，由所有的專案和編輯器呼叫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案組態的建置和部署作業的順序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供用於大多數的偵錯控制項的低階偵錯工具服務的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|可讓 VSPackages 存取目前選取項目的相關資訊，並讓與通訊**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的 UI 相關的 IDE 功能，例如建立和列舉的工具視窗或文件視窗，或向使用者報告錯誤的能力。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供 IDE 的狀態列上的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用來實作 automation 模型。  在專案模型中，您將會傳回內容物件，可讓您建立該物件的執行個體。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用來在專案中的物件階層架構中實作剪貼簿\] 的事件。  `SVsUIHierWinClipboardHelper`可讓您正確的控制代碼剪下、 複製及貼上作業。|  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-tw/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)