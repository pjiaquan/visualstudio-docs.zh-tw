---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令列工具，VSPerfCLREnv"
  - "命令列，工具"
  - "效能工具，VSPerfCLREnv"
  - "程式碼剖析工具，VSPerfCLREnv"
  - "VSPerfCLREnv 工具"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCLREnv 工具可用來設定對 .NET Framework 應用程式進行程式碼剖析時所需的三個環境變數。  這個工具使用下列語法：  
  
```  
VsPerfCLREnv [/option]  
```  
  
 您所選擇的選項將視使用的三種程式碼剖析類型而定：取樣、檢測或全域。  若要在程式碼剖析資料中包含層互動資料，就需要不同的選項。  下列表格描述每個選項的語法。  
  
> [!NOTE]
>  當您完成程式碼剖析之後，請執行 **VSPerfCLREnv** 搭配 **\/off** 或 **\/globaloff** 選項，刪除進行程式碼剖析所需的環境變數。  如需詳細資訊，請參閱稍後的「用來刪除環境設定的 VSPerfCLREnv 選項」。  
  
 **用於包含層互動資料的 VSPerfCLREnv 選項**  
  
> [!WARNING]
>  使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]，階層互動分析可以被收集。  不過，階層互動分析資料只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 和 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中檢視。  
  
 階層互動程式碼剖析提供關於 ADO.NET 查詢在多層應用程式中的其他資訊。  資料只會針對同步函式呼叫進行收集。  互動資料可以透過程式碼剖析方法加入到任何程式碼剖析執行。  
  
 **InteractionOn** 和 **GlobalInteractionOn** 選項可啟用層互動資料的收集功能。  在設定剖析應用程式所需的 VSPerfCLREnv 環境變數之後，就必須設定互動選項。  
  
 下列範例包含使用範例方法之程式碼剖析執行中的層互動資料：  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 下列範例包含執行 Windows 服務程式碼剖析的階層互動：  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **程序檢測程式碼剖析的 VSPerfCLREnv 選項**  
  
 下表描述檢測程式碼剖析的 VSPerfCLREnv 選項：  
  
|選項|說明|  
|--------|--------|  
|**TraceOn**|啟用使用檢測方法進行程式碼剖析。  請勿啟用記憶體配置剖析或收集物件存留期資料。|  
|**TraceGC**|啟用使用檢測方法進行記憶體配置剖析。  請勿啟用收集物件存留期資料的功能。|  
|**TraceGCLife**|啟用使用檢測方法進行記憶體配置剖析以及收集物件存留期資料。|  
  
 **程序取樣程式碼剖析的 VSPerfCLREnv 選項**  
  
 下表描述取樣程式碼剖析的 VSPerfCLREnv 選項：  
  
|選項|說明|  
|--------|--------|  
|**SampleOn**|啟用使用取樣方法進行程式碼剖析。  請勿啟用記憶體配置剖析或收集物件存留期資料。|  
|**SampleGC**|啟用使用取樣方法進行記憶體配置剖析。  請勿啟用收集物件存留期資料的功能。|  
|**SampleGCLife**|啟用使用取樣方法進行記憶體配置剖析。  此外也啟用收集物件存留期資料。|  
|**SampleLineOff**|停用 .NET 程式行層級的程式碼剖析資料收集。|  
  
 **全域程式碼剖析的 VSPerfCLREnv 選項**  
  
 若要對由作業系統啟動 \(不是由使用者啟動\) 的 Managed 服務 \(例如 ASP.NET Web 應用程式\) 進行程式碼剖析，請使用 VSPerfCLREnv 選項的全域程式碼剖析選項。  下表描述 VSPerfCLREnv 選項的全域版本。  這些選項可在登錄中設定適當環境變數。  
  
|選項|說明|  
|--------|--------|  
|**GlobalTraceOn**|啟用使用檢測方法進行全域程式碼剖析。  不收集記憶體配置事件或物件存留期資料。|  
|**GlobalTraceGC**|啟用使用檢測方法進行全域記憶體配置剖析。  請勿啟用收集物件存留期資料的功能。|  
|**GlobalTraceGCLife**|啟用使用檢測方法進行全域記憶體配置剖析。  此外也啟用物件存留期資料收集。|  
|**GlobalSampleOn**|啟用使用取樣方法進行全域程式碼剖析。  請勿啟用收集記憶體配置事件或物件存留期資料。|  
|**GlobalSampleGC**|啟用使用取樣方法進行全域記憶體配置剖析。  請勿啟用收集物件存留期資料的功能。|  
|**GlobalSampleGCLife**|啟用使用取樣方法進行全域記憶體配置剖析。  此外也啟用收集物件存留期資料。|  
  
 **用來刪除環境設定的 VSPerfCLREnv 選項**  
  
 完成 Managed 應用程式的程式碼剖析之後，請使用下列其中一個選項來刪除由 VSPerfCLREnv 加入的環境變數。  下表說明如何刪除標準和全域兩種環境變數：  
  
|選項|說明|  
|--------|--------|  
|**Off**|刪除標準 .NET 程式碼剖析的環境變數。  當非全域 VSPerfClrEnv 選項已經用於設定程式碼剖析工具環境變數時，請使用這個選項。|  
|**GlobalOff**|刪除全域 .NET 程式碼剖析的環境變數。  如果以作業系統 \(而非分析工具\) 來啟動應用程式，請使用這個選項。|  
  
## 備註  
 如果在 IDE 中使用 \[效能總管\] 來啟動應用程式，對 Managed 應用程式進行程式碼剖析時就不需要使用這些選項。  \[效能總管\] 會自動設定所有必要的環境設定。  
  
 如果進行程式碼剖析期間未設定正確的環境，分析期間會回報警告，而且 Managed 函式名稱將不會正確解析。  
  
## 請參閱  
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)