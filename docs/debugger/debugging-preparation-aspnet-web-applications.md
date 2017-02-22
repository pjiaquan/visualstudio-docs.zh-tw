---
title: "偵錯準備：ASP.NET Web 應用程式 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], Web 應用程式"
  - "偵錯 ASP.NET Web 應用程式"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯準備：ASP.NET Web 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網站範本可以建立 Web Form 應用程式。  當您使用這種範本建立網站時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會建立偵錯的預設設定。  您可以在 \[**專案屬性**\] 對話方塊中，指定是否將網頁設定為起始頁。  當您使用這些預設設定對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網站進行偵錯時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會啟動 Internet Explorer，並將該偵錯工具附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序 \(aspnet\_wp.exe 或 w3wp.exe\)。  如需詳細資訊，請參閱 [系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
### 若要建立 Web Form 網頁  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增網站**\]。  
  
2.  在 \[**新增網站**\] 對話方塊中，選取 \[[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **網站**\]。  
  
3.  按一下 \[**確定**\]。  
  
### 若要偵錯 Web Form  
  
1.  在函式和事件處理常式中設定一個或多個中斷點。  
  
     如需詳細資訊，請參閱[Breakpoints and Tracepoints](http://msdn.microsoft.com/zh-tw/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
2.  遇到中斷點時，逐步執行函式內的程式碼。  請觀察程式碼的執行，直到您找出問題癥結。  
  
     如需詳細資訊，請參閱[Stepping](http://msdn.microsoft.com/zh-tw/8791dac9-64d1-4bb9-b59e-8d59af1833f9)和[偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)。  
  
## 變更預設的組態  
 如果想要變更 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建立的預設偵錯和發行組態，您可以自行變更。  如需詳細資訊，請參閱[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
#### 若要變更預設偵錯組態  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下網站，並選取 \[**屬性頁**\] 開啟 \[**屬性頁**\] 對話方塊。  
  
2.  按一下 \[**起始選項**\]。  
  
3.  將 \[**起始動作**\] 設定為一開始要顯示的網頁。  
  
4.  確定已經選取 \[**偵錯工具**\] 下的 \[**ASP.NET 偵錯**\]。  
  
     如需詳細資訊，請參閱 [Web 專案的屬性頁設定](../debugger/property-pages-settings-for-web-projects.md)。  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)