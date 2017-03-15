---
title: "屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設定選項，請變更屬性"
  - "屬性頁"
  - "屬性頁中，變更設定選項"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 屬性頁
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用者可以檢視和變更使用屬性頁的專案組態相關且\-獨立屬性。  A **屬性頁** 中啟用按鈕 **屬性** 視窗或 \[方案總管\] 工具列上的屬性頁為提供檢視所選物件的物件。  屬性頁建立環境，並可供方案和專案。  它們，不過，也可以是開放的專案項目，請使用非組態相關屬性。  在專案中的檔案需要不同的編譯器參數才能正確建置時，可能會使用這項功能。  
  
## 使用屬性頁  
 如果已經顯示屬性頁，而且在選取範圍變更 \(例如，從專案到方案\)，以顯示新的選取項目的屬性變更的網頁中顯示的資訊。  如果物件上不支援屬性頁的屬性，\[屬性\] 頁面會是空的。  
  
 如果選取了多個物件，屬性頁會顯示所有選取的項目內容的交集。  如果選取的項目不包含組態相關屬性及**屬性頁**按一下在 \[方案總管\] 工具列上的按鈕時，焦點會變更 \[屬性\] 視窗。  與 \[屬性視窗\] 和 \[選取項目相關的詳細資訊，請參閱[擴充屬性](../../extensibility/internals/extending-properties.md)。  
  
 如果屬性將會顯示多個物件，並變更屬性頁中的值，會設定所有物件的值為新的值，即使最初不同而且頁面是空白時所顯示的個別物件的屬性。  
  
 有兩種一般性的**專案屬性頁**對話方塊中，您可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  首先，Visual Basic 專案而言，比方說，屬性頁會使用欄位的格式，如下列螢幕擷取畫面所示。  在第二個，稍後以顯示本章節中，屬性頁主機屬性方格類似於在 \[屬性\] 視窗中找到。  
  
 ![Visual Basic 屬性頁](../../extensibility/internals/media/vsvbproppages.png "vsVBPropPages")  
專案欄位格式\] 和 \[樹狀目錄結構與 \[屬性頁\] 對話方塊  
  
 在 \[屬性頁\] 對話方塊中的樹狀結構使用不建置<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。  環境中，根據層級的名稱傳遞給它的<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>介面，否則建置它。  
  
 有可用的只有兩個最上層類別[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]屬性頁：  
  
-   通用屬性，會顯示所選取的一或多個物件組態無關的資訊。  如此一來，選取其中一個常見的屬性子類別時，設定、 平台和組態管理員選項\] 對話方塊的頂端就無法使用。  
  
-   組態屬性，其包含了方案或專案的偵錯、 最佳化，以及建置參數與相關的組態相關資訊。  
  
 無法建立任何其他的最上層類別，但您可以選擇不想再顯示的實作中的其中一個`IVsPropertyPage`。  如果，比方說，您並沒有任何組態無關的屬性來顯示物件，您可以選擇不想再顯示 \[通用屬性\] 類別目錄。  如果顯示了通用屬性`ISpecifyPropertyPages`在實作時，會將從該項目的瀏覽的物件和組態屬性實作`ISpecifyPropertyPages`組態物件中 \(物件實作`IVsCfg`， `IVsProjectCfg`，以及相關的介面\)。  
  
 最上層\] 類別底下顯示的每一個類別代表一個個別的屬性頁。  類別和次類別使用中的項目\] 對話方塊中，由您的實作的`ISpecifyPropertyPages`和`IVsPropertyPage`。  
  
 `IDispatch`物件選取容器中已顯示在 \[屬性頁實作屬性的項目`ISpecifyPropertyPages`列舉類別識別碼的清單。  類別識別碼便當作變數來傳遞`ISpecifyPropertyPages` ，用於具現化的屬性頁。  類別識別碼的清單也會傳遞至`IVsPropertyPage`來建立對話方塊左邊的樹狀結構。  \[屬性頁\] 和 \[行程資訊備份到`IDispatch`實作物件`ISpecifyPropertyPages` ，並填滿每一頁的相關資訊。  
  
 瀏覽物件的屬性使用擷取`IDispatch`選取容器中的每一個物件。  
  
 實作`Help::DisplayTopicFromF1Keyword`在您的 VSPackage 提供 \[說明\] 按鈕的功能。  
  
 如需詳細資訊，請參閱`IDispatch`和`ISpecifyPropertyPages`MSDN library 中。  
  
 屬性頁的第二個型別顯示在範例主表單的 \[屬性\] 方格中，如下列螢幕擷取畫面所示。  
  
 ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
屬性頁對話方塊，並且屬性方格  
  
 介面`IVSMDPropertyBrowser`和`IVSMDPropertyGrid` \(vsmanaged.h 中所宣告的\) 用來建立並填入對話方塊或視窗中的 \[屬性\] 方格。  
  
 架構的專案已經大幅地從過去版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  特別是，哪一個專案的概念為作用中已變更。  在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，還有沒有使用中專案的概念。  在先前的開發環境中，使用中專案程式之專案的建置和部署指令時，會預設為上，無論內容。  現在，控制方案，並 arbitrates 的建置和部署指令套用至哪些專案。  
  
 那是先前使用中的專案現在中都找得到下列三種不同的方式：  
  
-   啟始專案  
  
     您可以指定專案或專案的方案，將會啟動，當使用者按下 F5 或從 \[建置\] 功能表中選取 \[執行\] 屬性頁。  這適用於類似於其名稱會顯示在 \[方案總管\] 中，以粗體字型，因為舊的使用中專案的方式。  
  
     您可以為自動化模型的屬性擷取啟始專案，藉由呼叫`DTE.Solution.SolutionBuild.StartupProjects`。  在 VSPackage 中，您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>方法。  `IVsSolutionBuildManager`做為服務，藉由使用`QueryService` SID\_SVsSolutionBuildManager 上。  如需詳細資訊，請參閱 [專案組態物件](../../extensibility/internals/project-configuration-object.md)和 [方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   現用方案組建組態  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]具有作用中方案組態的自動化模型，藉由實作`DTE.Solution.SolutionBuild.ActiveConfiguration`。  方案組態會包含每個專案方案 \(每個專案可以有多個組態，以不同名稱的多重平台\) 中的一個專案組態的集合。  方案屬性頁相關的詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   目前選取的專案  
  
     實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>方法來擷取專案階層架構和專案項目或選取的項目。  從 DTE，您可以使用`SelectedItems.SelectedItem.Project`和`SelectedItems.SelectedItem.ProjectItem`方法。  沒有核心的那些名下的範例程式碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的文件。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)