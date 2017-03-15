---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Events** 選項會控制 Windows 事件追蹤 \(ETW\) 記錄。  ETW 資料會儲存至與程式碼剖析工具資料檔案不同的 .etl 檔案。  使用 [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw 命令即可在報告中檢視這項資料。  
  
 在呼叫 VSPerfCmd **Shutdown** 命令以停止程式碼剖析前，可以隨時呼叫 **Events** 選項。  
  
## 語法  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### 參數  
 **On**&#124;**Off**  
 啟動或停止收集事件資料。  
  
 `Guid`  
 提供者控制項的 GUID。  
  
 `ProviderName`  
 已向 Windows Management Instrumentation \(WMI\) 註冊之提供者的名稱。  
  
 `Flags`  
 前置詞為 "0x" 的十六進位旗標值，由事件提供者定義。  
  
 `Level`  
 指定所收集的資料量。  `Level`是由事件提供者所定義。  
  
 **Events** 選項會將下列核心關鍵字解讀為提供者名稱：  
  
 **Process**  
 處理序事件  
  
 **Thread**  
 執行緒事件  
  
 **Image**  
 影像載入及卸載事件  
  
 **Disk**  
 磁碟 I\/O 事件  
  
 **File**  
 檔案 I\/O 事件  
  
 **Hardfault**  
 硬體分頁錯誤  
  
 **Pagefault**  
 軟體分頁錯誤  
  
 **Network**  
 網路事件  
  
 **Registry**  
 登錄存取事件  
  
 請注意，核心提供者必須處於啟用狀態。  在監視器關閉之前，核心提供者無法停用，其旗標也不能修改。  
  
## 備註  
  
> [!NOTE]
>  當 CLR ETW 事件啟用時，在追蹤檢視報告中也會收集額外的啟動資料。  若要排除啟動事件，不在報告中顯示，請使用下列命令：  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  由於這些事件未列在 Managed 物件格式 \(MOF\) 檔中，因此假如您不排除啟動事件，則這些事件在報告中便會顯示為 GUID。  如需詳細資訊，請參閱 Microsoft 網站上的下列網頁: [範例 Managed 物件格式 \(MOF\) \(MOF\) 檔案。](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)