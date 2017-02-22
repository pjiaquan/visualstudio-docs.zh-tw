---
title: "記憶體管理時間 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "並行視覺化檢視，分頁時間"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 記憶體管理時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

時間表中的這些區段是與分類為 \[記憶體管理\] 的封鎖時間相關聯。  這表示執行緒遭到與記憶體管理作業 \(例如分頁\) 相關聯的事件封鎖。  在這段時間，執行緒在「並行視覺化檢視」計為記憶體管理的 API 或核心狀態中被封鎖。  這些包括分頁和記憶體配置等事件。  
  
 若要進一步了解分類為分頁之封鎖的基本原因，請檢查相關聯的呼叫堆疊和程式碼剖析報告。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)