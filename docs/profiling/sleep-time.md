---
title: "睡眠時間 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "並行視覺化檢視, 睡眠時間"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 睡眠時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

時間表中的這些區段是與分類為睡眠的封鎖時間相關聯。  睡眠類別表示執行緒自動放棄其邏輯核心而且不執行任何作業。  在這段時間，執行緒在「並行視覺化檢視」計為睡眠的 API 中被封鎖。  `Sleep()` 和 `SwitchToThread()` 等 API 都屬於這個群組。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)