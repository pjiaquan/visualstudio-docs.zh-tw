---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log Devenv 參數"
  - "Devenv, /Log 參數"
  - "Log 參數 [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將所有活動記錄至記錄檔中，以進行疑難排解。  在您至少呼叫 `devenv /log` 一次之後這個檔案才會出現。  根據預設，此記錄檔為：  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Version*\\ActivityLog.xml  
  
 其中 *Version* 是 Visual Studio 的版本。  不過，您可以指定不同的路徑和檔案名稱。  
  
## 語法  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## 備註  
 這個參數必須出現在命令列結尾，位於所有其他參數之後。  
  
 只要是您使用 \/log 參數叫用的所有 Visual Studio 執行個體，都會為其寫入記錄。  但不會記錄沒有使用此參數所叫用的 Visual Studio 執行個體。  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)