---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean Devenv 參數"
  - "組建 [Team System], 清除檔案"
  - "清除 Devenv 參數"
  - "Devenv, /clean 參數"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清除所有中繼檔案和輸出目錄。  
  
## 語法  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## 引數  
 `FileName`  
 必要項。  方案檔案或專案檔案的完整路徑和名稱。  
  
 \/project `ProjName`  
 選擇項。  方案中專案檔的路徑和名稱。  您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑，或專案顯示的名稱，或專案檔的完整路徑和名稱。  
  
 \/projectconfig `ProjConfigName`  
 選擇項。  要在清除 `/project` 命名的專案時使用的專案建置設定名稱。  
  
## 備註  
 此參數執行和整合式開發環境內之 \[**清除方案**\] 功能表命令一樣的功能。  
  
 以雙引號括住包含空白的字串。  
  
 清除和建置的摘要資訊 \(包括錯誤\)，會顯示在 \[**命令**\] 視窗中，或任何用 `/out` 參數指定的記錄檔中。  
  
## 範例  
 第一個範例會使用方案檔中指定的預設組態清除 `MySolution` 方案。  
  
 第二個範例使用 `MySolution` 之 `Debug` 方案組態內的 `Debug` 專案組建組態，來清除 `CSharpConsoleApp` 專案。  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)