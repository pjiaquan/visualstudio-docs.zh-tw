---
title: "從命令列建立基本的分析報告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 從命令列建立基本的分析報告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明從 .vsp 或 .vsps 程式碼剖析資料檔案產生逗號分隔值 \(.csv\) 報告的基本 VSPerfReport 命令。  如需所有報告選項的說明，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
## 報告命令  
 使用下列其中一個命令，為指定的程式碼剖析資料檔建立報告。  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 為 .vsp 或 .vsps 產生所有可用的報告。  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 產生指定的報告類型。  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 產生列出每一個資料收集事件的報告。  僅限檢測。  
  
## 摘要報告類型參數  
 下表說明指定的報告類型選項產生的報告。  報告的資料行取決於用來收集資料的程式碼剖析方法。  
  
|摘要參數|報告描述|報告參考|  
|----------|----------|----------|  
|**CallerCallee**|代表函式之間的父\/子關聯性。|-   [取樣資料](../profiling/caller-callee-view-sampling-data.md)<br />-   [檢測資料](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|依照函式列出程式碼剖析資料。|-   [取樣資料](../profiling/functions-view-sampling-data.md)<br />-   [檢測資料](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/functions-view-contention-data.md)|  
|**CallTree**|代表執行程式碼剖析期間，函式的執行路徑以及程式碼剖析資料。|-   [檢測資料](../profiling/call-tree-view-instrumentation-data.md)<br />-   [取樣資料](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|列出執行程式碼剖析期間收集的程式碼剖析標記和 Windows 效能計數器的值。|-   [標記檢視](../profiling/marks-view.md)|  
|**Ip**|依照指令列出程式碼剖析資料。|-   [取樣資料](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [爭用資料](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|列出所配置物件的存留期。|-   [物件存留期檢視](../profiling/object-lifetime-view.md)|  
|**Line**|依照原始程式碼程式行列出程式碼剖析資料。|-   [取樣資料](../profiling/lines-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [爭用資料](../profiling/lines-view-contention-data.md)|  
|**Header**|程式碼剖析資料檔標頭資訊。|檔案專用。|  
|**Mark**|執行程式碼剖析期間收集的程式碼剖析標記。|-   [標記檢視](../profiling/marks-view.md)|  
|**Module**|列出模組的程式碼剖析資料。|-   [取樣資料](../profiling/modules-view-sampling-data.md)<br />-   [檢測資料](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/modules-view-contention-data.md)|  
|**Process**|列出處理序的程式碼剖析資料。|-   [處理序檢視](../profiling/process-view.md)<br />-   [爭用資料](../profiling/process-view-contention-data.md)|  
|**Thread**|列出執行緒的程式碼剖析資料。|-   [處理序檢視](../profiling/process-view.md)|  
|**Type**|依照型別列出配置程式碼剖析資料。|-   [配置檢視](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|資源爭用。|-   [資源爭用](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|列出效能規則問題。|-   列出規則問題的 CheckId、說明和原始程式碼位置。|  
|**ETW**|列出執行程式碼剖析期間收集的 Windows 事件追蹤 \(ETW\) 事件。|-   [ETW 報告](../profiling/event-tracing-for-windows-etw-report.md)|