---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r Devenv 參數"
  - "/run Devenv 參數"
  - "應用程式 [Visual Studio], 執行"
  - "Devenv, /run 參數"
  - "r Devenv 參數 (/r)"
  - "run Devenv 參數"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

編譯並執行指定的專案或方案。  
  
## 語法  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## 引數  
 `SolutionName`  
 必要項。  方案檔案的完整路徑和名稱。  
  
 `ProjectName`  
 必要項。  專案檔案的完整路徑和名稱。  
  
## 備註  
 根據使用中的方案組態指定之設定值進行編譯，並執行指定的專案或方案。  這個參數執行整合式開發環境 \(IDE\)，並在專案或方案已完成執行之後仍讓它繼續作用。  
  
-   以雙引號括住包含空白的字串。  
  
-   摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 這個範例使用主動式部署組態執行 `MySolution` 方案。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)