---
title: "開發 SharePoint 方案的要求"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 必要條件"
  - "Visual Studio 中的 SharePoint 開發, 需求"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 開發 SharePoint 方案的要求
  您必須在系統上安裝下列必要條件，才能使用 Visual Studio 隨附的 SharePoint 方案開發工具：  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] 或某個 Visual Studio Application Lifecycle Management \(ALM\) 版本。  
  
    -   安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 時選擇 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 功能 \(或兩者\)。  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 安裝在 64 位元 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 或 64 位元 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 上。  
  
     或  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 安裝在 64 位元 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 或 64 位元 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 上。  
  
> [!NOTE]  
>  只有在伺服器作業系統上由 SharePoint 正式支援時，兩種用戶端作業系統才被允許: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 和 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1。  如需詳細資訊，請參閱 [SharePoint Server 2010 開發人員工作站安裝指南](http://go.microsoft.com/fwlink/?LinkID=164557)。  
  
 「商務資料連接 \(BDC\) 模型」專案類型需要系統上安裝有 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
 若要在 Visual Studdio 中開發 SharePoint 方案，您必須在安裝了 Visual Studio 的相同電腦上安裝 SharePoint。  此外，SharePoint 開發人員工具僅支援 SharePoint 獨立組態，而不支援陣列\(遠端\)組態。  
  
> [!NOTE]  
>  在 Visual Studio 中的 SharePoint 專案僅支援 [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。  如果您為新 SharePoint 專案選取 [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)]，該專案仍會以 [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]為目標。  
  
 如需如何安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的詳細資訊，請參閱[安裝 Visual Studio](../Topic/Installing%20Visual%20Studio.md)。  
  
## Vista 與 Windows 7 使用者帳戶控制 \(UAC\)  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]與 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 合併了稱為User Account Contrl\(UAC\)的安全性功能。  若要在 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 系統上的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開發 SharePoint 方案，UAC 需要您以系統管理員的身分執行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  在桌面上，請開啟 \[[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\] 捷徑選單，然後選擇 \[**以系統管理員身分執行**\]。  
  
 若要設定桌面捷徑固定以系統管理員身分執行，請以滑鼠右鍵按一下該捷徑，然後依序選擇 \[**內容**\] 和 \[**進階**\] ，再選取 \[**以系統管理員身分執行**\]。  
  
 如需詳細資訊，請參閱[了解與設定 Windows Vista 中的使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)以及 [Windows 7 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## SharePoint 權限考量  
 若要開發 SharePoint 方案，您必須具備足夠的權限來執行和偵錯 SharePoint 方案。  測試 SharePoint 方案之前，請執行下列步驟，以確保您具備必要的權限：  
  
1.  在系統上以系統管理員身分加入您的使用者帳戶。  
  
2.  以 SharePoint 伺服器的 Farm Administrator 身分加入您的使用者帳戶。  
  
    1.  在 \[SharePoint 管理中心\] 中，選擇 \[**管理 Farm Administrators 群組**\] 連結。  
  
    2.  在 \[**型別陣列系統管理員**\] 頁面上，選擇 \[**新增**\] 按鈕。  
  
3.  將您的使用者帳戶加入至 WSS\_ADMIN\_WPG 群組。  
  
## 請參閱  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  