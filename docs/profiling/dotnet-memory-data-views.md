---
title: "程式碼剖析工具 .NET 記憶體資料檢視 | Microsoft Docs"
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
  - ".NET 記憶體分析方法檢視"
  - "程式碼剖析工具, .NET 記憶體分析檢視"
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 程式碼剖析工具 .NET 記憶體資料檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節包含程式碼剖析工具資料檔案之檢視和報告的參考資訊，這些檔案內含 .NET 記憶體程式碼剖析資料。  
  
## 在本節中  
 [摘要檢視](../profiling/summary-view-dotnet-memory-data.md)  
 列出配置最多記憶體的函式和型別。  
  
 [配置檢視](../profiling/dotnet-memory-allocations-view.md)  
 列出在程式碼剖析回合中配置的型別，以及導致型別配置的呼叫樹狀圖 \(執行路徑\)。  
  
 [物件存留期檢視](../profiling/object-lifetime-view.md)  
 列出在程式碼剖析回合中配置的型別，以及執行個體數目、位元組大小和型別的記憶體回收層代。  
  
 [呼叫樹狀圖檢視 \- 取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 顯示階層式樹狀結構，該樹狀結構代表在程式碼剖析回合中，函式的執行路徑以及記憶體配置資料。  
  
 [模組檢視 \- 取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 依照模組組織 .NET 記憶體配置資料，並列出配置記憶體時正在執行的函式、原始程式碼行及指令。  
  
 [呼叫端\/被呼叫端檢視 \- 取樣](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 針對所選取函式、呼叫所選取函式的函式，以及所選取函式呼叫的函式，列出記憶體配置資料。  
  
 [函式檢視 \- 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 列出執行程式碼剖析期間函式的記憶體配置資料。  
  
 [程式行檢視 \- 取樣](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 列出執行程式碼剖析期間，函式之原始程式碼行的記憶體配置資料。  
  
 [指令指標 \(IP\) 檢視 \- 取樣](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 列出執行程式碼剖析期間函式之指令的記憶體配置資料。  
  
 [呼叫樹狀圖檢視 \- 檢測](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 顯示階層式樹狀結構，該樹狀結構代表在程式碼剖析回合中，已檢測之函式的執行路徑、記憶體配置資料及詳細執行時間資料。  
  
 [模組檢視 \- 檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 依照模組組織程式碼剖析資料，並列出模組的函式、記憶體配置資料及詳細的執行時間資訊。  
  
 [呼叫端\/被呼叫端檢視 \- 檢測](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 針對所選取的檢測函式、呼叫所選取函式的函式，以及所選取函式呼叫的函式，列出記憶體配置資料和詳細的執行時間資訊。  
  
 [函式檢視 \- 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 列出執行程式碼剖析期間檢測函式的記憶體配置資料。  
  
## 參考  
 [函式詳細資料檢視](../profiling/function-details-view.md)  
 顯示所選函式與其呼叫端和被呼叫端函式之間的關聯圖。  
  
 [處理序檢視](../profiling/process-view.md)  
 列出處理序和執行緒的開始和結束時間。  
  
 [標記檢視](../profiling/marks-view.md)  
 列出已插入至程式碼剖析資料檔案的 ETW 和取樣事件。  
  
## 相關章節  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)  
 針對使用取樣方法所產生的程式碼剖析工具資料檔案，提供其檢視和報告的參考資訊。  
  
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)  
 針對使用檢測方法所產生的程式碼剖析工具資料檔案，提供其檢視和報告的參考資訊。