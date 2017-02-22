---
title: "認識程式碼剖析工具中的資源爭用資料值 | Microsoft Docs"
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
  - "並行分析方法"
  - "程式碼剖析工具，並行方法"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 認識程式碼剖析工具中的資源爭用資料值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

資源收集單元會在每次應用程式中的競爭執行緒被迫等候存取共用資源時，收集詳細的呼叫堆疊資訊。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 資源爭用報表會顯示爭用總數，以及發生等候之模組、函式、原始程式碼行和指令等候資源所花費的總時間。  
  
-   內含值顯示因資源爭用而強制函式等候的爭用總數，以及函式等候的總時間。函式呼叫之子函式所造成的爭用也包含在內含值中。  
  
-   專有值只顯示強制函式等候以及函式主體中的程式碼所造成的爭用總數。  子函式所造成的爭用則不包含在內。  此外，函式的專有時間也只包含函式主體中的陳述式所造成的等候時間。  
  
 資源爭用報表檢視也包含時間表圖形，顯示一段時間後的個別爭用事件，以及建立特定事件的呼叫堆疊。  如需詳細資訊，請參閱下列其中一個主題：  
  
-   [執行緒詳細資料檢視](../profiling/thread-details-view-contention-data.md)  
  
-   [資源詳細資料檢視](../profiling/resource-details-view-contention-data.md)  
  
 如需並行分析之另一個模式的詳細資訊，請參閱[並行視覺化檢視](../profiling/concurrency-visualizer.md)。