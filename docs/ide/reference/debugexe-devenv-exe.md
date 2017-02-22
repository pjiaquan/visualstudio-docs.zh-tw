---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
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
  - "/DebugExe [devenv.exe]"
  - "DebugExe 參數"
  - "Devenv, /DebugExe 參數"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開啟要進行偵錯的指定可執行檔。  
  
## 語法  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## 引數  
 `ExecutableFile`  
 必要項。  .exe 檔的路徑和檔名。  
  
 找不到 .exe 檔或該檔案不存在時，並不會顯示警告或錯誤，且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會正常啟動。  
  
## 備註  
 `ExecutableFile` 參數 \(Parameter\) 後面的任何字串都會傳遞至該檔案做為引數 \(Argument\)。  
  
## 範例  
 下列範例會開啟 `MyApplication.exe` 檔進行偵錯。  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)