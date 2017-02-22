---
title: "為方案建立父容器的資料夾 | Microsoft Docs"
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
  - "建立父容器的解決方案"
  - "原始檔控制外掛程式，建立父容器"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 為方案建立父容器的資料夾
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 \[原始檔控制外掛程式 API 1.2 版，使用者可以指定單一根原始檔控制項目的端方案中所有的 Web 專案。  超級統一根目錄 \(SUR\) 時，會呼叫這個單一的根目錄。  
  
 在 \[原始檔控制外掛程式 API 1.1 版中，如果使用者將多專案方案加入原始檔控制使用者收到提示來指定每個 Web 專案的一個原始檔控制項目的。  
  
## 新功能的旗標  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## 新函式  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 幾乎一定會 SUR 資料夾建立的方案加入至原始檔控制。  具體來說，它會在下列情況：  
  
-   專案是檔案共用 Web 專案。  
  
-   沒有專案和方案檔的不同磁碟機。  
  
-   有不同的共用專案和方案檔。  
  
-   分開 \(原始檔控制的方案\) 中加入專案。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建議 SUR 資料夾的名稱會與方案名稱相同但不包括副檔名。  下表摘要說明兩種版本的行為。  
  
|功能|tSource 控制外掛程式 API 版本 1.1|原始檔控制外掛程式的 API 版本 1.2|  
|--------|-------------------------------|---------------------------|  
|將方案加入 SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|將專案加入原始檔控制的方案|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio 的假設一個解決方案是 SUR.的直接子系|  
  
## 範例  
 下表列出了兩個範例。  在這兩種情況下， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會提示使用者輸入之前的原始檔控制方案的目的地位置 *user\_choice* 被指定為目的地。指定 user\_choice 時，會加入方案，且這兩個專案而不提示使用者輸入原始檔控制的目的地。  
  
|方案包含|在 \[磁碟位置|資料庫預設的結構|  
|----------|--------------|--------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\\Solutions\\sln1<br /><br /> C:\\Inetpub\\wwwroot\\Web1<br /><br /> \\\\server\\wwwroot$\\web2|$\/*user\_choice*\/sln1<br /><br /> $\/*user\_choice*\/C\/Web1<br /><br /> $\/*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\\Solutions\\sln1<br /><br /> D:\\Inetpub\\wwwroot\\Web1<br /><br /> C:\\solutions\\sln1\\Win1|$\/*user\_choice*\/sln1<br /><br /> $\/*user\_choice*\/D\/web1<br /><br /> $\/*user\_choice*\/sln1\/win1|  
  
 SUR 資料夾及子資料夾會建立無論是否已取消作業，或因錯誤而失敗。  它們不會自動移除在 \[取消\] 或錯誤條件。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]預設為版本 1.1 的表現，如果原始檔控制外掛程式不會傳回`SCC_CAP_CREATESUBPROJECT`和`SCC_CAP_GETPARENTPROJECT`功能旗標。  此外，使用者的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以選擇還原到版本 1.1 行為的下列機碼值設為 dword:00000001：  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateSolutionRootFolderInSourceControl"\= dword:00000001  
  
## 請參閱  
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)