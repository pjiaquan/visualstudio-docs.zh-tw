---
title: "檢查清單︰ 建立新的專案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，建立新的型別"
  - "專案類型，建立的檢查清單"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 檢查清單︰ 建立新的專案類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您必須完成幾項工作來建立新的專案類型。 下列檢查清單提供這些工作的指南。  
  
1.  設計新的專案類型的功能。 如需詳細資訊，請參閱[專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
2.  判斷程式碼和其他專案項目會使用的編輯器。 您可以使用核心或標準編輯器，或您可以建立並使用特定專案的編輯器。 如需詳細資訊，請參閱 [建立自訂編輯器和設計工具](../../extensibility/creating-custom-editors-and-designers.md) 與 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
3.  決定您的專案項目都會在的參與 **類別檢視** 和 **物件瀏覽器**。 如需詳細資訊，請參閱[支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
4.  衍生新類別，根據您先前為您的專案和專案項目做的設計決策。  
  
5.  撰寫下列專案類型元件的程式碼︰  
  
    -   專案 factory 來建立新的專案並開啟現有專案管理 如需詳細資訊，請參閱[使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。  
  
    -   專案階層架構和命令處理。 如需詳細資訊，請參閱 [不在建置中︰ 使用 HierUtil7 專案類別以實作專案類型 （c \+ \+）](http://msdn.microsoft.com/zh-tw/a5c16a09-94a2-46ef-87b5-35b815e2f346), ，[專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md), ，[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md) 和 [MenuCommand 對比 OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)。  
  
    -   專案項目管理，包括加入您的專案 **新的專案** 對話方塊。 如需詳細資訊，請參閱[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)與[註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
    -   持續性的專案狀態與個別項目。 如需詳細資訊，請參閱[開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。 持續性的解決方案資訊，請參閱 [方案](../../extensibility/internals/solutions.md)。  
  
    -   組態屬性\] 視窗中顯示的獨立屬性。 如需詳細資訊，請參閱[擴充屬性](../../extensibility/internals/extending-properties.md)。  
  
    -   若要顯示組態相關屬性的屬性頁中所實作的專案組態屬性。 如需詳細資訊，請參閱[管理組態選項](../../extensibility/internals/managing-configuration-options.md)。  
  
    -   列舉部署的輸出。 如需詳細資訊，請參閱[輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
    -   專案啟動服務。 如需詳細資訊，請參閱 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md) 與 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)。  
  
    -   物件或衍生自類別 `IDispatch`, 、 適用於自動化。  
  
    -   XML 命令資料表 \(.vsct\) 檔案。 如需詳細資訊，請參閱[Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
6.  測試、 偵錯，並啟動您的專案類型。  
  
7.  顯示您的專案中 **專案** \] 索引標籤的 **加入參考** \] 對話方塊中，藉由設定 `VARIANT_TRUE` 做為值 `VSHPROPID_ShowProjInSolutionPage`。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>與<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。  
  
8.  建立安裝程式 VSPackages Microsoft Installer \(.msi\) 檔案。 如需詳細資訊，請參閱[使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)、[註冊專案類型](../../extensibility/internals/registering-a-project-type.md)和[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## 請參閱  
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [何時建立專案類型](../../extensibility/internals/when-to-create-project-types.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)