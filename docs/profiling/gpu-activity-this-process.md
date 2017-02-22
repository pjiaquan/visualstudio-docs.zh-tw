---
title: "GPU 活動 (這個處理序) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU 活動 (這個處理序)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當GPU 在處理程序時，處理要求在執行緒檢視中的 \[**GPU 活動 \(這個處理序\)**\] 區段"並行視覺化檢視"表示時間。  這些要求被 GPU 送出，並且做為直接記憶體存取 \(DMA\) 的封包。  區段的長度表示時間 GPU 表示目前處理序的處理序 DMA 封包。  
  
 當您選取 GPU 分頁區段時，\[**目前**\] 索引標籤報表會顯示關於管理 DMA 封包的相關資訊。   這些資訊包括封包在硬體佇列中與 DirectX 引擎等候的時間、處理序和送出封包以及處理封包的時間。   刪除目前處理序之外的流程可能完全送出 DMA 封包寫入 GPU。  並行視覺化檢視可以偵測到另一個處理序何時送出工作交給 GPU 表示目前處理序。