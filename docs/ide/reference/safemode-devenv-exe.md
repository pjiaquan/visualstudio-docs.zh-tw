---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
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
  - "/SafeMode Devenv 參數"
  - "Devenv, /SafeMode 參數"
  - "SafeMode 參數"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在安全模式 \(Safe Mode\) 中啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，只載入預設的環境和服務。  
  
## 語法  
  
```  
devenv /SafeMode   
```  
  
## 備註  
 這個參數可在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 啟動時，阻止載入所有協力廠商的 VSPackage，以確保穩定執行。  
  
## 描述  
 下列範例會在安全模式中啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 程式碼  
  
```  
Devenv.exe /SafeMode  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)