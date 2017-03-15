---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具, 檢測設備"
  - "檢測設備, VSInstr 工具"
  - "分析工具, VSInstr"
  - "命令列工具, 檢測設備"
  - "命令列, 工具"
  - "VSInstr"
  - "VSInstr 工具"
  - "效能工具, VSInstr 工具"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSInstr 是用來檢測二進位檔的工具，  請使用下列語法叫用 \(Invoke\) 此工具：  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 下表說明 VSInstr 工具的選項：  
  
|選項|說明|  
|--------|--------|  
|**Help** 或 **?**|顯示說明。|  
|**U**|以 Unicode 格式撰寫已重新導向的主控台輸出。  它必須是第一個指定的選項。|  
|`@filename`|指定回應檔 \(Response File\) 名稱，該回應檔中的每一個程式行都包含一個命令。不要使用引號。|  
|**OutputPath** `:path`|指定已檢測之映像的目的目錄。  如果未指定輸出路徑，則會將原始二進位檔在相同目錄中重新命名成為新檔案 \(將 "Orig" 附加至檔案名稱\)，並對該二進位檔的複本進行檢測。|  
|**Exclude** `:funcspec`|指定要排除透過探查進行檢測的函式規格。  這在函式中的程式碼剖析探查插入導致無法預期或非預期的結果時很有用。<br /><br /> 請不要同時使用參考到相同二進位檔中之函式的 **Exclude** 和 **Include** 選項。<br /><br /> 您可以使用個別的 **Exclude** 選項指定多個函式規格。<br /><br /> `funcspec` 定義為：<br /><br /> \[namespace\<separator1\>\] \[class\<separator2\>\]function<br /><br /> 對於機器碼，\<separator1\> 是 `::`，而 Managed 程式碼則為 `.`。<br /><br /> \<separator2\> 永遠為 `::`。<br /><br /> **Exclude** 支援程式碼涵蓋範圍。<br /><br /> 支援萬用字元 \*。  例如，若要排除命名空間中的所有函式，請使用：<br /><br /> MyNamespace::\*<br /><br /> 您可以使用 **VSInstr \/DumpFuncs** 以指定的二進位列出函數的完整名稱。|  
|**Include** `:funcspec`|指定二進位檔中要用探查 \(Probe\) 檢測的函式規格。  二進位檔中的其他函式則不會受到檢測。<br /><br /> 您可以使用個別的 **Include** 選項指定多個函式規格。<br /><br /> 請不要同時使用參考到相同二進位檔中之函式的 **Include** 和 **Exclude** 選項。<br /><br /> **Include** 不支援程式碼涵蓋範圍。<br /><br /> `funcspec` 定義為：<br /><br /> \[namespace\<separator1\>\] \[class\<separator2\>\]function<br /><br /> 對於機器碼，\<separator1\> 是 `::`，而 Managed 程式碼則為 `.`。<br /><br /> \<separator2\> 永遠為 `::`。<br /><br /> 支援萬用字元 \*。  例如，若要在命名空間中包含所有函式，請使用：<br /><br /> MyNamespace::\*<br /><br /> 您可以使用 **VSInstr \/DumpFuncs** 以指定的二進位列出函數的完整名稱。|  
|**DumpFuncs**|列出指定映像內的函數。  但不會執行檢測。|  
|**ExcludeSmallFuncs**|從檢測中排除小型函式，也就是不會進行任何函式呼叫的精簡函式。  **ExcludeSmallFuncs** 選項可降低檢測負荷，從而加快檢測的速度。<br /><br /> 排除小型函式也可縮減 .vsp 檔案的大小以及分析所需的時間。|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|會插入剖析標記 \(用來分隔報告資料的識別項\)，供您用來識別 .vsp 報告檔中資料範圍的開始或結束。<br /><br /> **Before**  `` ：緊接在目標函式進入點之前。<br /><br /> **After**  `` ：緊接在目標函式結束碼後面。<br /><br /> **Top**  `` ：緊接在目標函式進入點之後。<br /><br /> **Bottom**  `` ：緊接在每次從目標函式返回之前。<br /><br /> `funcname` \- 目標函式的名稱。<br /><br /> `Markid` \- 正整數 \(型別為 long\)，做為程式碼剖析標記的識別項。|  
|**Coverage**|會執行涵蓋範圍的剖析。  它只能搭配下列選項使用：**Verbose**、**OutputPath**、**Exclude** 和 **Logfile**。|  
|**Verbose**|**Verbose** 是用來檢視有關檢測程序之詳細資訊的選項。|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|隱藏所有或特定的警告<br /><br /> `Message Number` \- 警告編號。  如果省略 `Message Number`，則會隱藏所有警告。<br /><br /> 如需詳細資訊，請參閱[VSInstr 警告](../profiling/vsinstr-warnings.md)。|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|指定下列 VSInstr 資料收集控制選項的程式碼剖析層級的選項：<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  ``  \- 指定執行緒層級的資料收集控制函式。  程式碼剖析只會針對目前的執行緒啟動或停止。  其他執行緒的程式碼剖析狀態不受影響。  預設值為 THREAD。<br /><br /> **Process**  ``  \- 指定處理序層級的程式碼剖析資料收集控制函式。  程式碼剖析會針對目前處理序中所有的執行緒啟動或停止。  其他處理序的程式碼剖析狀態不受影響。<br /><br /> **Global**  ``  \- 指定全域層級 \(跨處理序\) 的資料收集控制函式。<br /><br /> 如果您不指定程式碼剖析層級則會發生錯誤。|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|限制目標函式以及此函式所呼叫之子函式進行資料收集的選項。<br /><br /> **Inside**  ``  \- 在進入目標函式後立即插入 StartProfile 函式。  每次從目標函式返回之前，便立即插入 StopProfile 函式。<br /><br /> **Outside**  ``  \- 在每次呼叫目標函式之前立即插入 StartProfile 函式。  在每次呼叫目標函式之後立即插入 StopProfile 函式。<br /><br /> `funcname` \- 目標函式的名稱。|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|排除目標函式以及此函式所呼叫之子函式進行資料收集的選項。<br /><br /> **Inside**  ``  \- 在進入目標函式後立即插入 SuspendProfile 函式。  每次從目標函式返回之前，便立即插入 ResumeProfile 函式。<br /><br /> **Outside**  ``  \- 在進入目標函式之前立即插入 SuspendProfile 函式。  在離開目標函式之後立即插入 ResumeProfile 函式。<br /><br /> `funcname` \- 目標函式的名稱。<br /><br /> 如果目標函式包含 StartProfile 函式，則會在它之前插入 SuspendProfile 函式。  如果目標函式包含 StopProfile 函式，則會在它之後插入 ResumeProfile 函式。|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|在程式碼剖析執行期間開始資料收集。  它會在指定的位置插入 StartProfile API 函式。<br /><br /> **Before**  `` \- 緊接在目標函式進入點之前。<br /><br /> **After**  `` \- 緊接在目標函式結束碼後面。<br /><br /> **Top**  `` \- 緊接在目標函式進入點之後。<br /><br /> **Bottom**  `` \- 緊接在每次從目標函式返回之前。<br /><br /> `funcname` \- 目標函式的名稱。|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在程式碼剖析執行期間暫止資料收集。  它會在指定的位置插入 StopProfile 函式。<br /><br /> **Before**  `` \- 緊接在目標函式進入點之前。<br /><br /> **After**  `` \- 緊接在目標函式結束碼後面。<br /><br /> **Top**  `` \- 緊接在目標函式進入點之後。<br /><br /> **Bottom**  `` \- 緊接在每次從目標函式返回之前。<br /><br /> `funcname` \- 目標函式的名稱。|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在程式碼剖析執行期間暫止資料收集。  它會在指定的位置插入 SuspendProfile API 函式。<br /><br /> **Before**  `` \- 緊接在目標函式進入點之前。<br /><br /> **After**  `` \- 緊接在目標函式結束碼後面。<br /><br /> **Top**  `` \- 緊接在目標函式進入點之後。<br /><br /> **Bottom**  `` \- 緊接在每次從目標函式返回之前。<br /><br /> `funcname` \- 目標函式的名稱。<br /><br /> 如果目標函式包含 StartProfile 函式，則會在它之前插入 SuspendProfile 函式。|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在程式碼剖析執行期間開始或繼續資料收集。<br /><br /> 通常會在 **SuspendOnly** 選項已停止程式碼剖析之後用來開始程式碼剖析。  它會在指定的位置插入 ResumeProfile API 函式。<br /><br /> **Before**  `` \- 緊接在目標函式進入點之前。<br /><br /> **After**  `` \- 緊接在目標函式結束碼後面。<br /><br /> **Top**  `` \- 緊接在目標函式進入點之後。<br /><br /> **Bottom**  `` \- 緊接在每次從目標函式返回之前。<br /><br /> `funcname` \- 目標函式的名稱。<br /><br /> 如果目標函式包含 StopProfile 函式，則會在它之後插入 ResumeProfile 函式。|  
  
## 請參閱  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [VSInstr 警告](../profiling/vsinstr-warnings.md)   
 [程式碼剖析工具報表檢視](../profiling/performance-report-views.md)