---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/upgrade Devenv 參數"
  - "Devenv, /upgrade 參數"
  - "upgrade Devenv 參數"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將方案檔案和所有專案檔案，或指定的專案檔案，更新為這些檔案目前的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 格式。  
  
## 語法  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## 引數  
 `SolutionFile`  
 如果更新整個方案和其專案，是必要項。  方案檔案的路徑和名稱。  您可以只輸入方案檔案的名稱，或是輸入方案檔案的完整路徑和名稱。  如果資料夾或檔案名稱尚未存在，則會建立該資料夾或檔案。  
  
 `ProjectFile`  
 如果更新單一專案，是必要項。  方案中專案檔的路徑和名稱。  您可以只輸入專案檔案的名稱，或是輸入專案檔案的完整路徑和名稱。  如果資料夾或檔案名稱尚未存在，則會建立該資料夾或檔案。  
  
## 備註  
 備份會自動建立並複製到在目前目錄中建立的名為 Backup 的目錄中。  
  
 原始檔控制的方案或專案必須簽出後，才能進行升級。  
  
 使用 `/upgrade` 參數不會啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  升級的結果可以在方案或專案之開發程式語言的升級報告中查看。  沒有錯誤或使用資訊傳回。  如需在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中升級專案的詳細資訊，請參閱 [如何：不成功的 Visual Studio 專案升級疑難排解](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)。  
  
## 範例  
 這個範例會升級 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 方案預設資料夾中名為 "MyProject.sln" 的方案檔。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## 請參閱  
 [如何：不成功的 Visual Studio 專案升級疑難排解](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)