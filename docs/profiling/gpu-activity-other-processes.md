---
title: "GPU 活動 (其他處理序) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# GPU 活動 (其他處理序)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在並行視覺化檢視中執行緒檢視的 \[**GPU 活動 \(其他處理序\)**\] 區段表示 GPU 在這個系統裡處理來自其他處理序要求的時間。  這些要求被 GPU 所送出並且做為直接記憶體存取 \(DMA\) 的封包。區段的長度表示封包被 GPU 處理的持續時間。  
  
 當您選取這個區段時，\[**目前**\] 索引標籤報表會顯示關於管理封包的相關資訊。這些資訊包括封包在硬體佇列中與 DirectX 引擎等候的時間、處理序和送出封包以及處理封包的時間。