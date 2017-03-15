---
title: "管理部署的專案組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理部署的專案組態"
  - "專案 [Visual Studio SDK]，來管理部署的組態"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 管理部署的專案組態
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

部署是實際在組建程序的輸出項目移到預期的位置進行偵錯及安裝的行為。  比方說，Web 應用程式可能會在本機電腦上建置，並隨後被放在伺服器上。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種方式可以在部署中牽涉到的專案：  
  
-   為部署程序的主題。  
  
-   為部署程序管理員。  
  
 在部署解決方案之前，您必須先加入部署專案來設定部署選項。  如果部署專案並不存在，您會問您是否選取時，請建立一個**部署方案** 的 **建置**功能表或以滑鼠右鍵按一下方案。  按一下 \[ **是** 開啟 **加入新的專案** 對話方塊和 **遠端部署精靈**所選取專案。  
  
 遠端部署精靈詢問您有 \(視窗或網站\) 的應用程式的類型、 要包含的專案輸出群組、 您要加入任何其他檔案及您想要部署到遠端電腦。  在精靈的最後一頁會顯示選取的選項摘要。  
  
 是的部署程序主題的專案會產生必須移到其他的環境的輸出項目。  這些輸出項目就所謂的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>介面，其主要用途如果能讓專案加入至群組的輸出。  如需有關實作的`IVsProjectCfg2`，請參閱[輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
 部署專案，管理部署程序，請啟用 \[部署\] 命令，並選取此命令時回應。  部署專案實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面來執行部署，並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>介面，以報告部署狀態事件。  
  
 設定可以指定會影響其建置或部署作業的相依性。  建置或部署相依性是必須可以建置或部署之前或之後本身的組態會建置或部署的專案。  專案間的組建相依性將會說明與<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>介面，以及部署與相依性<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>介面。  如需詳細資訊，請參閱 [專案建置組態](../../extensibility/internals/project-configuration-for-building.md)。  
  
## 請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案建置組態](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)