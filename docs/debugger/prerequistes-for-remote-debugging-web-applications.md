---
title: "Web 應用程式遠端偵錯的必要條件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "偵錯 ASP.NET Web 應用程式, 遠端伺服器"
  - "遠端偵錯, 必要條件"
  - "遠端伺服器, 偵錯 Web 應用程式"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Web 應用程式遠端偵錯的必要條件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具，您就可以在本機電腦或遠端伺服器上無障礙地對 Web 應用程式進行偵錯。  這表示，偵錯工具的運作方式相同，並可讓您在任一部電腦上使用相同的功能。  不過，為了要讓遠端偵錯正確進行，有一些先決條件必須遵守。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 遠端偵錯元件必須安裝在您要偵錯的伺服器上。  如需詳細資訊，請參閱[設定遠端偵錯](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
-   根據預設，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序會以 ASPNET 使用者處理序的方式執行。  因此，您必須在執行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 的電腦上具有系統管理員權限，才能進行偵錯。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的名稱會隨著偵錯情節和 IIS 的版本而有所不同。  如需詳細資訊，請參閱 [如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
## 請參閱  
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)