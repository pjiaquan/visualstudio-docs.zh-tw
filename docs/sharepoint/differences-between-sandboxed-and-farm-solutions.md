---
title: "沙箱化方案與伺服器陣列方案之間的差異 | Microsoft Docs"
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
  - "陣列方案 [Visual Studio 中的 SharePoint 開發]"
  - "沙箱化方案 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 陣列方案"
  - "Visual Studio 中的 SharePoint 開發, 沙箱化方案"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 沙箱化方案與伺服器陣列方案之間的差異
  當編譯 SharePoint 方案時，它會部署至 SharePoint 伺服器，並附加偵錯工具進行偵錯。  用來對方案進行偵錯的方式取決於「沙箱化方案」屬性的設定：沙箱化方案或陣列方案。  
  
 如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
## 陣列方案  
 陣列方案在 IIS 背景工作處理序 \(W3WP.exe\) 中進行管理，會執行可影響整個陣列的程式碼。  當偵錯「沙箱化方案」屬性設定為「陣列方案」的 SharePoint 專案時，會在 SharePoint 擷取或部署功能之前，首先回收系統的 IIS 應用程式集區，以便釋放由 IIS 背景工作處理封鎖的任何檔案。  只會回收提供 SharePoint 專案網站 URL 的 IIS 應用程式集區。  
  
## 沙箱化方案  
 沙箱化方案在 SharePoint 使用者程式碼方案背景工作處理序 \(SPUCWorkerProcess.exe\) 中進行管理，執行只影響方案網站集合的程式碼。  因為沙箱化方案不會在 IIS 背景工作處理序中執行，所以無需重新啟動 IIS 應用程式集區或 IIS 伺服器。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將偵錯工具附加至 SPUCWorkerProcess 處理序，該處理序可由 SharePoint 中的 SPUserCodeV4 服務自動觸發和控制。  SPUCWorkerProcess 處理序不需要回收即可載入方案的最新版本。  
  
## 其中一種方案  
 使用其中一種方案，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 也會將偵錯工具附加至瀏覽器，以啟用用戶端指令碼偵錯。  為了達成這個目的，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會使用指令碼偵錯引擎。  若要啟用指令碼偵錯，您必須在收到提示時變更預設瀏覽器設定。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只會將偵錯工具附加至正在執行目前網站的 W3WP 或 SPUCWorkerProcess 處理序。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 也會附加 Managed COM Plus 和工作流程偵錯引擎。  
  
## 請參閱  
 [對 SharePoint 方案進行偵錯](../sharepoint/debugging-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)  
  
  