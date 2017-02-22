---
title: "註冊 Interop 組件命令處理常式 | Microsoft Docs"
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
  - "interop 組件，命令處理常式"
  - "命令使用 interop 組件，註冊處理"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 註冊 Interop 組件命令處理常式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 必須向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，以便在整合式的開發環境 \(IDE\) 正確路由傳送它的命令。  
  
 手動編輯，或使用註冊機構 \(.rgs\) 檔案，可以更新登錄。 如需詳細資訊，請參閱[Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)。  
  
 管理封裝架構 \(MPF\) 提供這項功能，透過 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 類別。  
  
 [Command Table Format Reference](http://msdn.microsoft.com/zh-tw/09e9c6ef-9863-48de-9483-d45b7b7c798f) 資源位於不受管理的附屬 dll UI。  
  
## 命令處理常式登錄的 VSPackage  
 做為使用者介面 \(UI\) 的處理常式的 VSPackage\-根據的命令需要登錄項目命名的 VSPackage `GUID`。 此登錄項目指定 VSPackage 的 UI 資源檔和該檔案中的功能表資源的位置。 登錄項目本身位於 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\Menus，其中 *\< 版本 \>* 的版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，例如 9.0。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 的根路徑*\< 版本 \>* 可以覆寫以替代根時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 殼層會初始化。 如需詳細的根路徑的詳細資訊，請參閱 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
### CTMENU 資源登錄項目  
 登錄項目結構是:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> 是 `GUID` 的格式為 {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX} VSPackage。  
  
 *\< 資源資訊 \>* 包含三個以逗號分隔的項目。 這些元素，順序如下:  
  
 \<*資源 DLL 路徑*\>，\<*功能表資源識別碼*\>，\<*功能表版本*\>  
  
 下表描述的欄位 \<*資源資訊*\>。  
  
|項目|描述|  
|--------|--------|  
|\<*資源 DLL 路徑*\>|這是資源包含功能表資源 DLL 的完整路徑，或保留為空白，表示 VSPackage 的資源 DLL 使用 \(如同在封裝子機碼係 VSPackage 本身中指定\)。<br /><br /> 這是慣用將此欄位保留空白。|  
|\<*功能表資源識別碼*\>|這是資源識別碼 `CTMENU` 資源，包含所有 UI 項目為 VSPackage 編譯從 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) 檔案。|  
|\<*功能表版本*\>|這是用做為版本號碼 `CTMENU` 資源。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用此值來判斷它是否需要 remerge 的內容 `CTMENU` 資源之所有其快取 `CTMENU` 資源。 Remerge 就會觸發執行 devenv 安裝命令。<br /><br /> 這個值應該一開始設定為 1 而且在每次變更後遞增 `CTMENU` 資源和 remerge 發生之前。|  
  
### 範例  
 以下是幾個資源項目範例:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令和使用 Interop 組件的功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)