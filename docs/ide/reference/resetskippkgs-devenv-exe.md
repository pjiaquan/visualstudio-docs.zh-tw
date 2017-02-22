---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs Devenv 參數"
  - "Devenv, /ResetSkipPkgs 參數"
  - "ResetSkipPkgs 參數"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

清除所有選項，以略過使用者加入至 VSPackage 的載入作業 \(若使用者不希望載入有問題的 VSPackage\)，然後啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 語法  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## 備註  
 若出現 SkipLoading 標記則會停用 VSPackage 的載入作業，而清除該標記則會重新啟用 VSPackage 的載入作業。  
  
## 範例  
 下列範例會清除所有 SkipLoading 標記。  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)