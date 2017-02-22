---
title: "核心檢視 | Microsoft Docs"
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
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "並行視覺化檢視，核心檢視"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 核心檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

核心檢視顯示執行緒執行是如何對應至邏輯處理器核心。  如果您要撰寫伺服器應用程式，這個檢視有助於透過執行緒親和性或執行緒集區管理，最佳化快取效能。  此外，也有助於將使用執行緒親和性實際上可能使跨核心移轉問題惡化的案例視覺化。  \[核心檢視\] 有兩個部分、圖形和一個圖例。  
  
 上方圖形在 Y 軸顯示邏輯核心，而在 X 軸顯示時間。  在圖形中的每個執行緒都有唯一的色彩，以便進行一段時間的追蹤其跨核心的移動。  您可以選取圖例區域篩選圖形中的執行緒。  
  
 圖例區域中有圖形上每個色彩的相對項目。  每個項目會顯示執行緒色彩和名稱、跨核心內容切換次數、內容切換總數，以及跨核心內容切換的百分比。  圖例是依據跨核心內容切換次數遞減排序。  它會列出在顯示的時間範圍期間，執行中的執行緒。如果縮放或移動瀏覽，清單會更新。  
  
## 請參閱  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)   
 [使用率檢視](../profiling/utilization-view.md)   
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)