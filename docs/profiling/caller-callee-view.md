---
title: "呼叫端/被呼叫端檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "程式碼剖析工具，報表，呼叫端/被呼叫端檢視"
  - "程式碼剖析工具，呼叫端/被呼叫端檢視"
  - "效能報告，呼叫端/被呼叫端檢視"
  - "呼叫端/被呼叫端檢視"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# 呼叫端/被呼叫端檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[呼叫端\/被呼叫端\] 檢視會顯示所選取函式以及其父函式和子函式的程式碼剖析資訊。  \[呼叫端\/被呼叫端\] 檢視包含 3 個方格：  
  
 中間的方格顯示 \[**目前的函式**\]，會列出所選取函式的程式碼剖析資訊。  這些值包括執行程式碼剖析期間所收集之函式的所有呼叫。  
  
 \[**呼叫目前函式的函式**\] 會顯示在上方的方格中，並列出呼叫端 \(父\) 函式呼叫所產生的選取 \(目前\) 函式值的數目。  
  
 下方的方格顯示 \[**目前的函式所呼叫的函式**\]，會列出目前函式在呼叫所選取函式的子函式 \(即被呼叫端\) 時，該子函式的程式碼剖析資訊。  
  
 \[呼叫端\/被呼叫端\] 檢視中會出現的資料行，取決於收集資料時使用的程式碼剖析方法 \(取樣或檢測\)，以及在執行程式碼剖析期間是否有收集 .NET 記憶體資料。  
  
 您可以按兩下檢視中其他兩個部分列出的任何一個函式，以選擇讓不同的函式變成 \[報告\] 檢視中間部分的 \[目前的函式\]。  \[報告\] 檢視將會自動更新以反映變更。  
  
 您可按一下資料行名稱以排序資料。  您可以在 \[呼叫端\/被呼叫端\] 檢視中加入其他資料行。  如需詳細資訊，請參閱[如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
## 請參閱  
 [呼叫端\/被呼叫端檢視](../profiling/caller-callee-view-sampling-data.md)   
 [呼叫端\/被呼叫端檢視](../profiling/caller-callee-view-instrumentation-data.md)   
 [呼叫端\/被呼叫端檢視 \- 檢測](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [呼叫端\/被呼叫端檢視 \- 取樣](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [呼叫端\/被呼叫端檢視](../profiling/caller-callee-view-contention-data.md)