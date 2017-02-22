---
title: "資源監視效能規則 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 資源監視效能規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

資源監視分類中的效能訊息會提供有關應用程式效能的其他資料。  您可以使用這項資料來分析效能問題。  這些規則屬於告知性，而且會針對每個程式碼剖析回合報告。  
  
|||  
|-|-|  
|[DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|這個訊息回報處理器忙於執行應用程式指令的時間百分比。  回報的值就是進行程式碼剖析之處理序處於作用中狀態的所有測量間隔的平均值。|  
|[DA0502：進行程式碼剖析之處理序所需的最大 CPU 使用量](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|這個訊息回報處理器忙於執行應用程式指令的最大時間百分比。  回報的值是要程式碼剖析之處理序處於作用中狀態的所有測量間隔所回報的最大值。|  
|[DA0503：進行程式碼剖析之處理序的平均工作集 \(以位元組為單位\)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|這個訊息回報程式碼剖析處於作用中狀態時處理序所使用的平均實體記憶體數量 \(以位元組為單位\)。  這個實體記憶體的度量也稱為工作集。|  
|[DA0504：進行程式碼剖析之處理序的最大工作集 \(以位元組為單位\)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|這個訊息回報程式碼剖析處於作用中狀態時處理序所使用的最大實體記憶體數量 \(以位元組為單位\)。|  
|[DA0505：為進行程式碼剖析的處理序所配置的平均私用位元組](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|這個訊息回報程式碼剖析處於作用中狀態時處理序所配置的平均虛擬記憶體數量 \(以位元組為單位\)。  這個虛擬記憶體的度量也稱為「*私用位元組*」\(Private Byte\)。  私用位元組代表由處理序所配置而且只能供在處理序內部執行之執行緒存取的虛擬記憶體位置。|  
|[DA0506：為進行程式碼剖析的處理序所配置的最大私用位元組](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|這個訊息回報程式碼剖析處於作用中狀態時處理序所配置的最大虛擬記憶體數量 \(以私用位元組為單位\)。|