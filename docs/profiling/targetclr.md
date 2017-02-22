---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當有多個 Common Language Runtime \(CLR\) 版本載入到應用程式時，**TargetCLR** 選項會指定要進行程式碼剖析的 CLR 版本。  
  
 根據預設，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具會以應用程式載入的第一個 CLR 版本為目標。  
  
## 語法  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### 參數  
 `ClrVersion`  
 CLR 的版本號碼。  請使用版本格式 **vN.N.NNNNN**。  
  
## 必要選項  
 **TargetCLR** 選項只能搭配 **Launch**  或 **Attach** 選項使用。  
  
 **Launch:** `AppName`  
 啟動指定的應用程式並開始程式碼剖析。  
  
 **Attach:** `PID`  
 開始對指定的處理序進行程式碼剖析。  
  
## 範例  
 在這個範例中，TargetCLR 選項是用來確定 CLR 4.0.11003 版已進行程式碼剖析。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```