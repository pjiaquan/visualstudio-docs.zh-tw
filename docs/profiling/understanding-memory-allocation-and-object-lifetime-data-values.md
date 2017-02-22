---
title: "認識程式碼剖析工具中的記憶體配置和物件存留期資料值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 記憶體分析方法"
  - "程式碼剖析工具，.NET 記憶體方法"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 認識程式碼剖析工具中的記憶體配置和物件存留期資料值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*.NET memory allocation* 中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]程式碼剖析工具會收集在配置中建立或在記憶體回收中終結之物件大小和數目的相關資訊，以及事件發生時有關函式「*呼叫堆疊*」\(Call Stack\) 的其他資訊。  「*呼叫堆疊*」\(Call Stack\) 是一種動態結構，存放有關處理器正在執行的函式之資訊。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 每次在進行程式碼剖析的應用程式中配置 .NET Framework 物件時，記憶體配置的程式碼剖析方法都會中斷電腦處理器。  如果同時收集物件存留期資料，則分析工具會在每次 .NET Framework 記憶體回收後中斷處理器。  每個經過程式碼剖析的函式和每個物件類型的資料都會加以彙總。  
  
## 配置資料  
 發生 .memory 事件時，配置和終結的記憶體物件的總計數和大小都會累加。  
  
 發生 .memory 配置事件時，程式碼剖析工具會累加呼叫堆疊上每一個函式的樣本計數。  收集資料時，呼叫堆疊上只有一個函式會在其函式主體中執行程式碼。  堆疊上的其他函式是函式呼叫階層中，等待所呼叫函式回傳的父系。  
  
-   針對配置事件，程式碼剖析工具會累加目前執行其指令之函式的「*專有*」\(Exclusive\) 樣本計數。  由於專有樣本也是函式樣本總計 \(「*內含*」\(Inclusive\)\) 的一部分，因此目前使用中函式的內含樣本計數也會累加。  
  
-   程式碼剖析工具會針對呼叫堆疊上所有其他函式遞增內含樣本計數。  
  
## 存留期資料  
 .NET Framework 的記憶體回收行程會管理您應用程式記憶體的配置和釋放。  為了要最佳化記憶體回收行程的效能，Managed 堆積分成三個層代 \(Generation\)：0、1 和 2。  執行階段的記憶體回收行程會將新的物件儲存在第 0 個層代。  在回收之後存留下來的物件則會升階並儲存在第 1 個和第 2 個層代。  
  
 記憶體回收行程會藉由取消配置物件的整個層代，回收記憶體。  對於經過程式碼剖析的應用程式所建立的物件，\[物件存留期\] 檢視會顯示其數目，以及在回收這些物件時的物件大小和層代大小。