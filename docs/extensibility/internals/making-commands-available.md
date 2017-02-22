---
title: "提供可用的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "功能表 [Visual Studio SDK] 命令"
  - "最佳作法、 功能表和工具列命令"
  - "工具列 [Visual Studio]，最佳作法"
  - "功能表命令，最佳作法"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# 提供可用的命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

多個 VSPackages 新增至 Visual Studio 時，可能會變得過擁擠使用者介面 \(UI\) 命令。 您可以程式設計您的封裝，以協助降低這個問題，請如下:  
  
-   程式封裝以便載入只有當使用者需要它。  
  
-   程式封裝，使其命令才會顯示在整合式的開發環境 \(IDE\) 的目前狀態的內容中可能會需要它們。  
  
## 延遲載入  
 若要啟用的一般方式延遲載入是設計的 VSPackage，讓它的命令會顯示在 UI 中，但封裝本身不會載入直到使用者按一下其中一個命令。 若要達成此目的，.vsct 檔案中，建立不具有任何命令旗標的命令。  
  
 下列範例會顯示來自.vsct 檔的功能表命令定義。 這是 Visual Studio 封裝範本所產生的命令時 **功能表命令** 選取範本中的選項。  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 在範例中，如果父群組， `MyMenuGroup`, ，是最上層功能表的子系，例如 **工具** \] 功能表，此命令會顯示在該功能表上，但直到使用者按一下此命令時，將不會載入之封裝的執行命令。 但是，透過程式設計來實作命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，您可以啟用封裝以載入第一次展開的功能表命令時。  
  
 請注意延遲的載入也可改善啟動效能。  
  
## 目前的內容和命令的可見性  
 您可以程式設計 VSPackage 命令要顯示或隱藏，根據 VSPackage 資料或目前相關的動作的目前狀態。 您可以啟用狀態進行設定其命令，通常使用的實作 VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 方法從 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，但這需要才能夠執行程式碼要載入 VSPackage。 相反地，我們建議您啟用 IDE 管理命令的可見性，而不載入封裝。 若要這樣做，.vsct 檔案中，關聯一個或多個特殊的 UI 內容中的命令。 這些 UI 內容由稱為 GUID 識別 *命令內容 GUID*。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視所產生的使用者動作，例如載入專案，或編輯要建置變更。 發生變更時，會自動修改 IDE 的外觀。 下表顯示 IDE 的四個主要內容變更， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視。  
  
|內容的型別|描述|  
|-----------|--------|  
|使用中的專案類型|對於大部分的專案類型，這 `GUID` 值是可實作專案 VSPackage 的 GUID 相同。 不過， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 專案使用 \[專案類型 `GUID` 做為值。|  
|使用中視窗|一般而言，這是最近一次的主動式文件視窗，以建立索引鍵繫結的目前 UI 內容。 不過，它也可能是類似於內部的 Web 瀏覽器的索引鍵繫結資料表的工具視窗。 例如，HTML 編輯器的多個索引標籤的文件視窗，如每個索引標籤都有一個不同的命令內容 `GUID`。|  
|作用中的語言服務|目前顯示在文字編輯器中的檔案與相關聯之語言服務。|  
|使用中工具視窗|已開啟，而且具有焦點的視窗。|  
  
 第五個主要內容區域是 IDE 的 UI 狀態。 作用中的命令內容來識別 UI 內容 `GUID`s，如下所示:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 這些 Guid 會標示為作用中或非作用中，根據 IDE 的目前狀態。 在相同的時間可以使用多個 UI 的內容。  
  
### 隱藏和顯示內容為基礎的命令  
 您可以顯示或隱藏在 IDE 中的封裝\] 命令，而不載入封裝本身。 若要這樣做，請定義命令.vsct 檔的封裝中使用 `DefaultDisabled`, ，`DefaultInvisible`, ，和 `DynamicVisibility` 命令旗標並新增一或多個 [VisibilityItem](../../extensibility/visibilityitem-element.md) 項目 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 一節。 當指定的命令內容 `GUID` 會變成作用中，此命令會顯示不含載入封裝。  
  
### 自訂內容的 Guid  
 如果未定義的 GUID 不適當的命令內容中，您可以定義在 VSPackage 中，然後進行程式設計，讓它成為作用中或非作用中，視需要控制命令的可見性。 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務:  
  
-   註冊內容 Guid \(藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 方法\)。  
  
-   取得內容的狀態 `GUID` \(藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法\)。  
  
-   開啟內容 `GUID`s 開啟和關閉 \(藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 方法\)。  
  
    > [!CAUTION]
    >  請確定，VSPackage 不會影響任何現有內容 GUID 的狀態因為其他 VSPackages 可能需要使用它們。  
  
## 範例  
 VSPackage 命令的下列範例會示範動態的可見性，其中一個命令，而不載入 VSPackage 由命令的內容。  
  
 命令是設定為啟用，而且方案存在，只要顯示亦即，每當下列的命令內容 Guid 的其中一個是使用中:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 在範例中，請注意，每個命令旗標是個別 [命令旗標](../../extensibility/command-flag-element.md) 項目。  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 也請注意，必須在個別指定每個 UI 內容 `VisibilityItem` 項目，如下所示。  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## 請參閱  
 [MenuCommand 對比 OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)   
 [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)