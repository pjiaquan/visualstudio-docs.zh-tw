---
title: "原始檔控制外掛程式 API 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式，函式"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 原始檔控制外掛程式 API 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

原始檔控制外掛程式 API 提供下列函式，必須實作的原始檔控制外掛程式根據此 API。 每個函式和語意 \(semantics\) 的簽章相關聯的位元旗標，此參照中詳細說明的其他參數。  
  
## 初始設定和維護函式  
  
|函式|描述|  
|--------|--------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|關閉專案。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示使用者輸入指定命令的進階選項。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|傳回的新版的原始檔控制外掛程式。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化原始檔控制外掛程式。 每個外掛程式執行個體一次呼叫它。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|開啟專案。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|泛型的函式，用來設定各種不同的選項。 每個選項的開頭 `SCC_OPT_xxx` 而且有它自己組定義的值。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|呼叫一次當原始檔控制外掛程式必須已被拔除。|  
  
## 核心原始檔控制功能  
  
|函式|描述|  
|--------|--------|  
|[SccAdd](../extensibility/sccadd-function.md)|將陣列的原始檔控制系統的完整的路徑名稱所指定的檔案。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|可讓使用者瀏覽已在原始檔控制系統的檔案，然後將這些檔案目前的專案。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|檢查陣列中的檔案。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|簽出檔案的陣列。|  
|[SccDiff](../extensibility/sccdiff-function.md)|顯示本機使用者的完整的路徑名稱和原始檔控制下的版本所指定的檔案之間的差異。|  
|[SccGet](../extensibility/sccget-function.md)|擷取一組檔案的唯讀複本。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|會檢查呼叫端要求相關的檔案狀態 \(透過 `SccQueryInfo`\)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|會使原始檔控制外掛程式，以提示使用者輸入有意義的外掛程式的專案路徑。|  
|[SccHistory](../extensibility/scchistory-function.md)|顯示歷程記錄完整的本機檔案名稱的陣列。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|會檢查其目前狀態的檔案清單。 此外，使用 `pfnPopulate` 函式的檔案不相符的準則時，通知呼叫端 `nCommand`。|  
|[SccProperties](../extensibility/sccproperties-function.md)|顯示完整的檔案屬性。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|會檢查其目前狀態的完整檔案清單。|  
|[SccRemove](../extensibility/sccremove-function.md)|從原始檔控制系統中移除完整格式的檔案的陣列。|  
|[SccRename](../extensibility/sccrename-function.md)|新名稱重新命名指定的檔案，在原始檔控制系統。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|存取完整的原始檔控制系統的功能。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|復原簽出檔案的陣列。|  
  
## 支援其他功能 \(1.2 版的原始檔控制外掛程式 API\) 的函式  
 此群組的函式定義的原始檔控制外掛程式 API 1.2 版中包含的其他功能。 它們提供更進階的原始檔控制功能和功能存取權。  
  
|函式|描述|  
|--------|--------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|啟動批次作業。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|建立具有指定名稱，現有的父專案下的子專案。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|顯示本機使用者的完整的路徑名稱和原始檔控制資料庫位置所指定的目錄之間的差異。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|會檢查其目前狀態的完整目錄的清單。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|結束批次作業。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|傳回父路徑指定的專案 \(專案必須存在\)。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|檢查是否允許多重簽出檔案。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|檢查是否外掛程式將會建立 MSSCCPRJ。SCC 檔案。|  
  
## 支援進階的功能 \(1.3 版的原始檔控制外掛程式 API\) 的函式  
 此群組的函式定義的原始檔控制外掛程式 API 1.3 版中包含的其他功能。 它們提供更進階的原始檔控制功能和功能存取權。  
  
|函式|描述|  
|--------|--------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|從原始檔控制中加入目前專案的檔案清單。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|從原始檔控制不含使用者介面中擷取檔案的清單。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|擷取一份不同的本機檔案的原始檔控制檔案。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|擷取指定原始檔控制外掛程式所支援的擴充的功能的旗標。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|擷取使用者特定的選項。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|檢查目錄和檔案的專案或專案原始檔控制下的清單。 找到的每個目錄和檔案名稱會傳遞至回呼函式。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|會檢查檔案的清單名稱變更。 每個檔案名稱會傳遞至其變更狀態的回呼函式。|  
  
## 需求  
 標頭: scc.h  
  
 \(環境 SDK 中提供的公用資料夾中，根據預設，包含 *\[磁碟機\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc; VSIP MSSCCI 範例中，資料夾中也提供 *\[磁碟機\]*\\Program Files\\VSIP 8.0\\MSSCCI\)。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)