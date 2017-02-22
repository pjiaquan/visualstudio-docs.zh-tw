---
title: "空白時間表區段 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "並行視覺化檢視，空白時間表區段"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 空白時間表區段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

並行視覺化檢視內，時刻表的區段為空白 \(有白色背景\) 原因相依於這種通道。  
  
-   對於 CPU 執行緒通道，表示這個部分執行緒在時間表的過程中不存在。  如果您對執行緒有興趣，您可以使用縮放控制項或水平捲動尋找其執行部分。  
  
-   如需 I\/O 通道，表示目標處理序期間發生該時間點，磁碟沒有存取。  
  
-   對於 DirectX 通道，表示目標處理序中執行時間表的持續期間，這部分 GPU 未工作。  
  
-   對於標記通道，表示標記不會產生。  
  
## 請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)   
 [縮放控制 \(執行緒檢視\)](../profiling/zoom-control-threads-view.md)