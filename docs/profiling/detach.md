---
title: "中斷連結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 中斷連結
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Detach** 選項會將程式碼剖析工具與指定的處理序 \(如果沒有指定則為所有處理序\) 中斷連結。  程式碼剖析必須是使用取樣方法所初始化的。  
  
 以 **Launch** 或 **Attach** 選項啟動的程式碼剖析，可以利用 **Detach** 來中斷連結。  程式碼剖析工具可以使用後續的 **Attach** 命令來重新附加。  
  
 **Detach** 不會關閉程式碼剖析資料檔案。  使用 **Shutdown** 選項可以結束程式碼剖析，並關閉資料檔案。  
  
> [!NOTE]
>  如果 **Start** 選項和 **Crosssession** 選項一起指定，則對 **VSPerfCmd \/Attach** 或 **VSPerfCmd \/Detach** 的任何呼叫也必須指定 **Crosssession**。  
  
## 語法  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### 參數  
 `PIDs|ProcessNames`  
 `PID` \- 一個或多個處理序的數字系統識別項。  
  
 `ProcessNames` \- 處理序名稱。  如果具名處理序的多個執行個體正在執行，則結果無法預期。  
  
 請以逗點分隔多個處理序。  
  
 如果未指定處理序，則程式碼剖析工具會從所有經過程式碼剖析的處理序中斷連結。  
  
## 有效的選項  
 下列 **VSPerfCmd** 選項可以在單一命令列中搭配 **Attach** 選項使用。  
  
 **Crosssession**  
 啟用登入工作階段以外工作階段的程式碼剖析應用程式。  如果 **Start** 選項與 **Crosssession** 選項一起指定，則為必要項。  
  
## 範例  
 在這個範例中，**Detach** 命令會暫止程式碼剖析，而 **Shutdown** 命令會關閉程式碼剖析工具資料檔案。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)