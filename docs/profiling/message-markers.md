---
title: "訊息標記 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 訊息標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

訊息標記表示記錄輸出。  訊息是由特定的執行緒在特定時間發行的字串。  您可以匯出訊息至文字檔以搭配其他工具使用。  您可以放置一個訊息的指標在 \[並行視覺化檢視\] 以檢視訊息字串。  然後您可以在 [標記報告](../profiling/markers-report.md)中檢視所有訊息的標記。下圖將顯示一個訊息的標記。  
  
## 訊息彙總資料標記  
 有時候多個訊息在"並行視覺化檢視"下發生的非常相近，因此不能被個別繪製。  發生這種情況時，表示基礎訊息的 *訊息彙總標記* 會顯示。  當您停留指標在這些圖示的其中一個時，工具提示會顯示基礎訊息的訊息數目。  若要檢視此訊息，請放大。如果您一直放大和仍然取得彙總資料標記，即可檢視在 [標記報告](../profiling/markers-report.md)內的基本訊息。  
  
## 請參閱  
 [並行視覺化檢視中的標記](../profiling/concurrency-visualizer-markers.md)   
 [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)