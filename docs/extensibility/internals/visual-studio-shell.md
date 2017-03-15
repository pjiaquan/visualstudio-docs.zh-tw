---
title: "Visual Studio Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "殼層，Visual Studio"
  - "Visual Studio 中，命令介面"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 殼層是主要的代理程式中的整合 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 介面會提供必要的功能，讓 VSPackages 共用通用的服務。 因為架構的目標 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 背心 VSPackages 中的主要功能是殼層是一種架構提供基本功能和支援 VSPackages 其元件之間的互通。  
  
## 殼層責任  
 殼層具有下列重要的責任︰  
  
-   支援 （透過 COM 介面） 的基本使用者介面 \(UI\) 項目。 這些包括預設功能表和工具列、 文件視窗框架或多重文件介面 \(MDI\) 子視窗，和工具視窗框架，以及停駐支援。  
  
-   為了協調文件的持續性，並保證在一個以上的方式，或以不相容的方式，就無法開啟該文件時，維護所有目前開啟的文件中執行文件資料表 \(RDT\) 的執行清單。  
  
-   支援的命令路由和命令處理介面， `IOleCommandTarget`。  
  
-   在適當的時間載入 Vspackage。 延遲載入 VSPackage 是為了改善效能的殼層。  
  
-   管理特定的共用服務，例如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, ，這樣會提供基本的殼層功能和 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, ，提供基本的視窗化功能。  
  
-   管理方案 \(.sln\) 檔案。 方案會包含相關的專案，類似於在 Visual c \+ \+ 6.0 的工作區 \(.dsw\) 檔案群組。  
  
-   追蹤整個殼層的選取項目、 內容和貨幣。 殼層會追蹤下列項目類型︰  
  
    -   目前的專案  
  
    -   目前的專案項目或項目目前的識別碼。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   目前的選取範圍 **屬性** 視窗或 `SelectionContainer`  
  
    -   UI 內容 Id 或控制命令、 功能表和工具列的可見性的 CmdUIGuids  
  
    -   目前使用中的項目，例如使用中視窗、 文件，並復原管理員  
  
    -   磁碟機 \[動態說明使用者內容屬性  
  
 殼層也會調解安裝的 VSPackages 與目前的服務之間的通訊。 它支援的殼層的核心功能，讓它們能夠以中整合的所有 VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 這些核心功能包括下列項目︰  
  
-   **有關** 對話方塊方塊和開頭顯示畫面  
  
-   **新增並加入現有項目** 對話方塊  
  
-   **類別檢視** 視窗和 **物件瀏覽器**  
  
-   **參考** 對話方塊  
  
-   **文件大綱** 視窗  
  
-   **動態說明** 視窗  
  
-   **尋找** 和 **取代**  
  
-   **開啟專案** 和 **開啟檔案** 對話方塊上 **新增** 功能表  
  
-   **選項** 對話方塊 **工具** 功能表  
  
-   **屬性** 視窗  
  
-   **方案總管**  
  
-   **工作清單** 視窗  
  
-   **工具箱**  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Vspackage](../../extensibility/internals/vspackages.md)