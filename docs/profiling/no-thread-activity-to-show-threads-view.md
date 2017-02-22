---
title: "沒有執行緒活動可顯示 (執行緒檢視) | Microsoft Docs"
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
  - "vs.cv.threads.nothreadreport"
helpviewer_keywords: 
  - "並行視覺化檢視, 沒有執行緒活動可顯示 (執行緒檢視)"
ms.assetid: aa5ae9d0-561d-4ef8-b36b-258ce553d50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 沒有執行緒活動可顯示 (執行緒檢視)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個區域會顯示有關目前可見時間範圍內未隱藏執行緒的資料。  
  
 如果沒有顯示任何資訊，請檢查下列設定：  
  
-   縮放層級是否過高？  請嘗試縮小或捲動，以便在此範圍內呈現更多執行緒活動。  
  
-   是否隱藏過多執行緒？  如果是，請嘗試顯示所有執行緒  
  
-   如果您選取了 \[**Just My Code**\]，就只能檢視有關您自己程式碼的資料。  請嘗試清除此設定，以便確定是否存在任何系統執行緒活動。  
  
-   請確定 \[減少雜訊\] 設定為低臨界值。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)