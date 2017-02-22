---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project Devenv 參數"
  - "部署專案, 指定"
  - "Devenv, /project 參數"
  - "project Devenv 參數 (/project)"
  - "專案 [Visual Studio], 建置"
  - "專案 [Visual Studio], 清除"
  - "專案 [Visual Studio], 重建"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

識別在指定之方案組態中要建置、清除、重建或部署的單一專案。  
  
## 語法  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## 引數  
 \/build  
 建置由 `/project` `ProjName` 指定的專案。  
  
 \/clean  
 清除在建置期間建立的所有中繼檔案和輸出目錄。  
  
 \/rebuild  
 清除然後建置由 `/project` `ProjName` 指定的專案。  
  
 \/deploy  
 指定在建置或重建後要部署的專案。  
  
 `SolnConfigName`  
 必要項。  方案組態的名稱會套用到 `SolutionName` 中命名的方案。  
  
 `SolutionName`  
 必要項。  方案檔案的完整路徑和名稱。  
  
 \/project `ProjName`  
 選擇項。  方案中專案檔的路徑和名稱。  您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑，或專案顯示的名稱，或專案檔的完整路徑和名稱。  
  
 \/projectconfig `ProjConfigName`  
 選擇項。  要套用到 `/project` 命名之專案建置設定的名稱。  
  
## 備註  
  
-   必須使用 `devenv /build`、\/`clean`、`/rebuild` 或 `/deploy` 命令的一部分。  
  
-   以雙引號括住包含空白的字串。  
  
-   建置的摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案建置設定，建置 `CSharpConsoleApp` 專案。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)