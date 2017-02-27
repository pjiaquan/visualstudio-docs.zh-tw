---
title: "如何：偵錯 Web 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET Web Form, 偵錯"
  - "ASP.NET, 偵錯 Web 應用程式"
  - "偵錯 ASP.NET Web 應用程式, 開發期間"
  - "Web 服務, 偵錯"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# 如何：偵錯 Web 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開發 Web 應用程式的主要技術。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具提供在本機環境或遠端伺服器上，偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式所用的強大工具。  本主題說明如何在開發期間偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 專案。  如需如何對已部署在實際執行伺服器 \(Production Server\) 上的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式進行偵錯的詳細資訊，請參閱[偵錯已部署的 Web 應用程式](../debugger/debugging-deployed-web-applications.md)。  
  
 若要偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式：  
  
-   您必須具有必要的使用權限。  如需詳細資訊，請參閱 [系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
-   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 偵錯必須在 \[**專案屬性**\] 中啟用。  
  
-   應用程式的組態檔 \(Web.config\) 必須設為偵錯模式。  偵錯模式會導致 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 產生動態產生之檔案的符號，並使偵錯工具附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式。  如果您已從 Web 專案範本建立專案，則 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會在開始偵錯時自動設定這個項目。  
  
-   如需詳細資訊，請參閱 [如何：啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)。  
  
### 若要在開發期間偵錯 Web 應用程式  
  
1.  按一下 \[**偵錯**\] 功能表上的 \[**啟動**\]，開始偵錯 Web 應用程式。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會建置 Web 應用程式專案、視需要部署應用程式、如果您在本機偵錯，則會啟動 ASP.NET 程式開發伺服器，以及附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  
  
2.  使用偵錯工具來設定和清除中斷點、逐步執行和執行其他偵錯作業，就和您使用任何應用程式一樣。  
  
     如需詳細資訊，請參閱[偵錯工具基礎](../debugger/debugger-basics.md)。  
  
3.  在 \[**偵錯**\] 功能表上按一下 \[**停止偵錯**\] 以結束偵錯工作階段，或是在 Internet Explorer 的 \[**檔案**\] 功能表上按一下 \[**關閉**\]。  
  
## 請參閱  
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)   
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [如何：啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)