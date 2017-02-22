---
title: "/LCID (devenv.exe) | Microsoft Docs"
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
  - "/l Devenv 參數"
  - "/lcid Devenv 參數"
  - "Devenv, /LCID 參數"
  - "預設語言"
  - "LCID devenv 參數"
  - "地區設定 ID"
  - "地區設定 ID, IDE 的設定"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定整合式開發環境 \(IDE\) 內，文字、貨幣和其他數值所使用的預設語言。  
  
## 語法  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## 引數  
 `LocaleID`  
 必要項。  您所指定語言的 LCID \(地區設定 ID\)。  
  
## 備註  
 載入 IDE 並設定環境的預設自然語言。  這項變更會持續在工作階段之間，並反映於 IDE 中 \[**選項**\] 對話方塊的 \[**環境**\] 選項中的 \[**國際設定**\] 窗格。  
  
 如果指定的語言在使用者的系統上無法使用，\/LCID 參數就會被忽略。  
  
 下表列出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援之語言的 LCID。  
  
|Language|LCID|  
|--------------|----------|  
|中文 \(簡體\)|2052|  
|中文 \(繁體\)|1028|  
|英文|1033|  
|法文|1036|  
|德文|1031|  
|義大利文|1040|  
|日文|1041|  
|韓文|1042|  
|西班牙文|3082|  
  
## 範例  
 這個範例載入具有英文來源字串的 IDE。  
  
```  
devenv /LCID 1033  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [選項對話方塊、環境、國際設定](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)