---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**GC** 選項會啟用 .NET Framework 記憶體配置和物件存留期資料的收集功能。  **GC** 選項只能搭配取樣程式碼剖析方法以及 **Launch** 選項使用。  
  
 使用 **GC** 選項時，不需要 VSPerfClrEnv **\/sampleon** 命令。  
  
 如果未指定參數，或是指定 **Allocation** 參數，則只會收集 .NET Framework 記憶體配置資料。  如果指定 **Lifetime** 參數，則會同時收集 .NET Framework 記憶體配置和 .NET Framework 物件存留期資料。  
  
## 語法  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### 參數  
 **Allocation**  
 預設值。  收集 .NET Framework 記憶體配置資料。  
  
 **Lifetime**  
 同時收集 .NET Framework 記憶體配置資料和 .NET Framework 物件存留期資料。  
  
## 必要選項  
 **GC** 選項只能與 **Launch** 選項搭配使用。  
  
 **Launch:** `AppName`  
 啟動指定的應用程式並以取樣方法開始執行程式碼剖析。  
  
## 範例  
 下列範例會啟動應用程式並收集 .NET Framework 記憶體配置資料。  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)