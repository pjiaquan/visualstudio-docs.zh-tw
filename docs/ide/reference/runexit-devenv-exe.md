---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit Devenv 參數"
  - "Devenv, /runexit 參數"
  - "runexit Devenv 參數"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

編譯並執行指定的專案或方案，然後關閉整合式開發環境 \(IDE\)。  
  
## 語法  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## 引數  
 `SolutionName`  
 必要項。  方案檔案的完整路徑和名稱。  
  
 `ProjectName`  
 必要項。  專案檔案的完整路徑和名稱。  
  
## 備註  
 根據使用中的方案組態指定之設定值進行編譯，並執行指定的專案或方案。  在執行專案或方案時，這個參數會最小化 IDE，且在專案或方案完成執行之後關閉 IDE。  
  
-   以雙引號括住包含空白的字串。  
  
-   摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 這個範例使用主動式部署組態，在最小化的 IDE 中執行 `MySolution` 方案，然後關閉 IDE。  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)