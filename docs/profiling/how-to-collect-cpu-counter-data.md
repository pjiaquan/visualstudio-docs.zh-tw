---
title: "如何：使用檢測方法收集 CPU 計數器資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "程式碼剖析工具，使用可移植的 CPU 計數器"
  - "效能工具，可移植的 CPU 計數器"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用檢測方法收集 CPU 計數器資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CPU 事件計數器可用來收集硬體的相關效能資料。  當您使用檢測程式碼剖析方法時，這個主題顯示如何收集事件計數器資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 會發生兩種 CPU 計數器事件：  
  
-   可移植的事件 \- 不論是哪一種型號的 CPU 都可以收集到的 CPU 事件。  
  
-   平台事件 \- 特定型號 CPU 專有的 CPU 事件。  
  
 可移植的事件包括一般事件 \(例如 Instructions Retired 和 Non Halted Cycles\)、CPU 緩衝事件、分支事件和 L2 快取事件。  可用的平台事件計數器是由處理器製造商決定。  
  
 事件分類可以在可移植的計數器和平台計數器之間共用。  例如，下列資料分類常見於這兩種類型：  
  
-   記憶體事件。  
  
-   前端事件。  
  
-   分支事件。  
  
 您可以在程式碼剖析工具中透過下列兩種方式來收集效能計數器資料：  
  
-   在透過檢測進行程式碼剖析時，從一個或多個計數器收集資料。  
  
-   在透過取樣進行程式碼剖析時，指定計數器事件做為取樣間隔。  如需詳細資訊，請參閱[如何：選擇取樣事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)。  
  
### 若要在您透過檢測進行程式碼剖析時收集 CPU 效能計數器資料  
  
1.  在效能工作階段 \[**屬性頁**\] 上，按一下 \[**CPU 計數器**\]。  
  
2.  選取 \[**收集 CPU 計數器**\] 核取方塊。  
  
3.  展開 \[**可用的效能計數器**\] 樹狀目錄，直到您找到想要收集的取樣事件為止。  
  
4.  針對您想收集的每個事件，選取該事件，並按一下向右箭號，將事件加入至 \[**選取的計數器**\] 清單。  
  
    > [!NOTE]
    >  只有當您選取 \[**收集 CPU 計數器**\] 核取方塊時，\[**可用的效能計數器**\] 才會啟用。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)   
 [如何：選擇取樣事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)