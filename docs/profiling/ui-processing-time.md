---
title: "UI 處理時間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "並行視覺化檢視, UI 處理時間"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# UI 處理時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

時間表中的這些區段是與分類為 UI 處理的封鎖時間相關聯。  這表示執行緒正在提取 Windows 訊息或執行其他使用者介面 \(UI\) 工作。  在這段時間，執行緒在「並行視覺化檢視」計為 UI 處理的 API 中被封鎖。  `GetMessage()` 和 `MsgWaitForMultipleObjects()` 等 API 都屬於這個群組。  
  
 如果沒有識別預先定義的封鎖 API，請檢閱呼叫堆疊和程式碼剖析報告，判斷延遲的根本原因。  
  
 「UI 處理」類別對於了解 GUI 應用程式的回應很重要，而且適用於依賴 UI 回應的應用程式。  例如，如果應用程式中的 UI 執行緒在「UI 處理」中達到 100% 時間，表示回應狀況可能非常良好。  不過，如果 UI 執行緒在其他類別花了大量時間，則請尋找根本原因並考慮在該執行緒上減少非 UI 類別的選項。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)