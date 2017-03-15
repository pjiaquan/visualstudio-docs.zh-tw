---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy Devenv 參數"
  - "deploy Devenv 參數"
  - "部署應用程式 [Visual Studio], 建置後"
  - "Devenv, /deploy 參數"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在建置或重建後部署方案。  本項只適用於 Managed 程式碼專案。  
  
## 語法  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## 引數  
 `SolnConfigName`  
 必要項。  用來建置在 `SolutionName` 中命名之方案的方案組態名稱。  
  
 `SolutionName`  
 必要項。  方案檔案的完整路徑和名稱。  
  
 \/project `ProjName`  
 選擇項。  方案中專案檔的路徑和名稱。  您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑，或專案顯示的名稱，或專案檔的完整路徑和名稱。  
  
 \/projectconfig `ProjConfigName`  
 選擇項。  要在建置 `/project` 命名的專案時使用的專案建置設定名稱。  
  
## 備註  
 指定的專案必須是部署專案。  如果指定的專案不是部署專案，在傳遞已建置的專案以部署時，會因錯誤而失敗。  
  
 以雙引號括住包含空白的字串。  
  
 建置的摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 此範例使用 `MySolution` 的 `Release` 方案組態中的 `Release` 專案建置設定，部署 `CSharpConsoleApp` 專案。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)