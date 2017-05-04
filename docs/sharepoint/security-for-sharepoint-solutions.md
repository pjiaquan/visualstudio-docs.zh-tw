---
title: "SharePoint 方案的安全性 | Microsoft Docs"
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
  - "安全性 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 安全性"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint 方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會納入下列功能，來協助增強 SharePoint 應用程式的安全性。  
  
## 安全控制項項目  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立的每個 SharePoint 專案項目都具有一個 \[**安全控制項項目**\] 屬性，用來代表安全控制項集合。  其 \[**安全**\] 子屬性可讓您指定您認為安全控制項。  如需詳細資訊，請參閱 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 和 [指定安全 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177521)。  
  
## AllowPartiallyTrustedCallers 屬性  
 根據預設，只有受執行階段程式碼存取安全性 \(CAS\) 系統完全信任的應用程式才可以存取共用的 Managed 程式碼組件。  以 AllowPartiallyTrustedCallers 屬性標記完全受信任的組件可以允許部分信任的組件對其進行存取。  
  
 AllowPartiallyTrustedCallers 屬性會加入至未部署至系統全域組件快取 \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) 的任何 SharePoint 方案。  這包含沙箱化方案或部署至 SharePoint 應用程式 Bin 目錄的方案。  如需詳細資訊，請參閱 [版本 1. 的 Microsoft .NET Framework 安全性變更](http://go.microsoft.com/fwlink/?LinkId=177515) 和 [部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
## 防止指令碼威脅屬性  
 「*指令碼插入*」\(Script Injection\) 是指潛在的惡意程式碼插入控制項或網頁。  為了協助防止 SharePoint 2010 網站受到指令碼入侵，預設情況下，參與者無法檢視或編輯 Web 組件或其屬性。  此行為受到名為 SafeAgainstScript 之 SafeControl 屬性的控制。  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，於專案項目的 \[**安全控制項項目**\] 子屬性 \[**防止指令碼威脅**\] 中設定此屬性。  如需詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)與[如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)。  
  
## Vista 與 Windows 7 使用者帳戶控制  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 加入了一項名為「使用者帳戶控制」\(User Account Control，UAC\) 的安全性功能。  若要在 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 系統上的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開發 SharePoint 方案，UAC 需要您以系統管理員的身分執行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  從 \[**開始**\] 選單中，開啟 \[[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\] 的捷徑功能表，然後選取 \[**以系統管理員身份執行**\]。  
  
 若要設定 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 捷徑永遠以系統管理員身份執行，請開啟其捷徑功能表，選擇 \[**屬性**\]，選取 \[**屬性**\] 對話方塊中的 \[**進階**\] 按鈕，然後選取 \[**以系統管理員身分執行**\] 核取方塊。  
  
 如需詳細資訊，請參閱[了解與設定 Windows Vista 中的使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkID=156476)以及 [Windows 7 使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## SharePoint 權限考量  
 若要開發 SharePoint 方案，您必須具備足夠的權限來執行和偵錯 SharePoint 方案。  測試 SharePoint 方案之前，請執行下列步驟，以確保您具備必要的權限：  
  
1.  在系統上以系統管理員身分加入您的使用者帳戶。  
  
2.  以 SharePoint 伺服器的 Farm Administrator 身分加入您的使用者帳戶。  
  
    1.  在 \[SharePoint 2010管理中心\] 中，選擇 \[**管理型別陣列系統管理員群組**\] 連結。  
  
    2.  在 \[**型別陣列系統管理員**\] 頁面上，選取 \[**新增**\] 功能表選項  
  
3.  將您的使用者帳戶加入至 WSS\_ADMIN\_WPG 群組。  
  
## 其他安全性資源  
 如需安全性問題的詳細資訊，請參閱下列內容。  
  
### Visual Studio 安全性  
  
-   [安全性和使用者權限](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Native 和 .NET Framework 程式碼中的安全性](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [.NET Framework 中的安全性](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### SharePoint 安全性  
  
-   [SharePoint Foundation 管理和安全性](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint 安全性資源中心](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [保護 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [改善 Web 應用程式安全性:威脅與對策](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### 一般安全性  
  
-   [MSDN 安全程式開發週期](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [建置安全的 ASP.NET 應用程式：驗證、授權和安全通訊](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  