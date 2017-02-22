---
title: "CPU 使用率圖形 | Microsoft Docs"
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
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "CPU 使用率圖形並行視覺化檢視，CPU 使用率圖形"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CPU 使用率圖形
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CPU 使用率圖形說明了應用程式在一段時間內的並行層級。   X 軸代表應用程式的持續時間，而 Y 軸代表系統上的邏輯核心數目。   此圖形無法明確指出任何指定時刻上的特定使用中核心。   例如，如果兩個核心各以 50% 的容量在一段指定的時間內執行，這個檢視則只會顯示一個邏輯核心在使用中。  
  
## CPU 使用率圖形色彩  
  
-   綠色表示已進行過程式碼剖析之應用程式在系統中耗用邏輯核心的部分。  
  
-   黃色表示系統上其他處理序所耗用的邏輯核心。   如果圖形中黃色所佔的百分比很高，就表示其他處理序的系統負載很重，而且您的處理序可能會被它們優先佔用。   若要減少其他處理序所耗用的邏輯核心，請減少它們在系統上執行的數目。  
  
-   紅色表示系統處理序所耗用的邏輯核心。   雖然您無法直接控制這個項目，不過知道發生這種情況的時間很有用，因為它可能會影響您的處理序是否能使用邏輯核心。  
  
-   灰色表示系統上還有未使用到的邏輯核心可供分配使用。   如果您可以找到更多平行處理原則的機會，您的處理序就可以使用這些核心。  
  
## 請參閱  
 [使用率檢視](../profiling/utilization-view.md)   
 [平均 CPU 使用率](../profiling/average-cpu-utilization.md)