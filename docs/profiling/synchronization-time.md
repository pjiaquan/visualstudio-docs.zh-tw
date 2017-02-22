---
title: "同步處理時間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "並行視覺化檢視, 同步處理時間"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 同步處理時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

時間表中的這些區段是與分類為同步處理的封鎖時間相關聯。  如果某個執行緒在同步處理時標記為封鎖，就表示下列其中一件事：  
  
-   執行緒的執行可能已經導致系統呼叫已知的執行緒同步處理 API，例如 `EnterCriticalSection()` 或 `WaitForSingleObject()`。  
  
-   API 比對演算法不完整，因此某些可對應至其他分類的 API 可能也會顯示成同步處理，因為呼叫堆疊中的某個框架最後會到達已對應至此分類的基礎核心封鎖基本型別。  
  
 若要了解執行緒封鎖事件的基本原因，請仔細地檢查封鎖呼叫堆疊和分析報表。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)