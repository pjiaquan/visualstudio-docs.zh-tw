---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
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
  - "/ResetSettings Devenv 參數"
  - "Devenv, /ResetSettings 參數"
  - "ResetSettings 參數"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

還原 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 預設設定，並自動啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  選擇性地將設定重設為指定的 .vssettings 檔。  
  
 預設設定取決於第一次啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時所選取的設定檔。  
  
## 語法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## 引數  
 `SettingsFile`  
 要套用至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 .vssettings 檔完整路徑和名稱。  
  
 若要還原 \[一般開發設定\] 設定檔，請使用 `General`。  
  
## 備註  
 如果未指定 `SettingsFile`，則會在下次啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時提示您選取預設的設定集合。  
  
## 範例  
 下列命令列會套用儲存在 `MySettings.vssettings` 檔中的設定。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## 請參閱  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)