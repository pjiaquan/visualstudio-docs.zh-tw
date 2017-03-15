---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild Devenv 參數"
  - "應用程式 [Visual Studio], 重建"
  - "Devenv, /rebuild 參數"
  - "專案 [Visual Studio], 重建"
  - "rebuild Devenv 參數 (/rebuild)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清除然後建置指定的方案組態。  
  
## 語法  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## 引數  
 `SolnConfigName`  
 必要項。  用來重建在 `SolutionName` 中命名之方案的方案組態名稱。  
  
 `SolutionName`  
 必要項。  方案檔案的完整路徑和名稱。  
  
 \/project `ProjName`  
 選擇項。  方案中專案檔的路徑和名稱。  您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑，或專案顯示的名稱，或專案檔的完整路徑和名稱。  
  
 \/projectconfig `ProjConfigName`  
 選擇項。  要在重建 `/project` 命名的專案時使用的專案建置設定名稱。  
  
## 備註  
  
-   此參數執行和整合式開發環境內之 \[**重建方案**\] 功能表命令一樣的功能。  
  
-   以雙引號括住包含空白的字串。  
  
-   清除和建置的摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案建置設定，清除並重建 `CSharpWinApp` 專案。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)