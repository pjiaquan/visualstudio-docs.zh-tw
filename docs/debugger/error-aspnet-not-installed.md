---
title: "錯誤：尚未安裝 ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, 安裝錯誤訊息"
  - "偵錯工具, Web 應用程式錯誤"
  - "錯誤訊息, ASP.NET"
  - "Web 應用程式, 錯誤"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：尚未安裝 ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 時，就會發生這個錯誤。  這可能表示從未安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或是先安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 之後才安裝 IIS。  
  
### 若要重新安裝 ASP.NET  
  
1.  從 \[命令提示字元\] 視窗，執行下列命令：  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     其中 *version* 代表您電腦上所安裝 .NET Framework 的版本號碼，例如 v1.0.370。  您可以查看 `\WINDOWS\Microsoft.NET\Framework` 目錄，來決定 .NET Framework 的版本。  
  
    > [!NOTE]
    >  您可以利用 Windows Server 2003 \[控制台\] 中的 \[**新增或移除程式**\] 來安裝 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。  
  
## 請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)