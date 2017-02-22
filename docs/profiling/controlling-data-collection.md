---
title: "在程式碼剖析工具中控制資料收集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼剖析工具的進階工作"
  - "程式碼剖析工具, 進階工作"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在程式碼剖析工具中控制資料收集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具讓您可以控制在效能工作階段期間收集程式碼分析資料的時機，並指定要進行程式碼分析的函式。  本節描述如何從 \[**效能總管**\] 與 \[**資料收集控制**\] 視窗啟動和停止資料收集，以及如何限定為程式碼分析資料收集的物件。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**開始及停止程式碼分析**：您可以在應用程式啟動時，開始對應用程式進行程式碼分析，或者將分析工具附加至正在執行的處理序。  當目標應用程式正在執行時，您可以暫停和繼續資料收集。  關閉目標應用程式或中斷程式碼分析工具與執行中處理序的連結，即可結束程式碼分析工作階段。|-   [如何：啟動和結束程式碼剖析](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [如何：為執行中的處理序附加和中斷連結程式碼剖析工具](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [如何：暫停和繼續程式碼剖析](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)|  
|**設定檢測分析以限制收集的資料**：您可以使用效能工作階段組態屬性，限制使用檢測方法執行程式碼分析期間所收集的資料。  您可以包含或排除特定 .dll 檔案、命名空間、類別和函式。  您也可以排除不符合所指定大小臨界值的函式。|-   [如何：限制檢測特定 DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [如何：從檢測排除或包含 Short 函式](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)|  
  
## 相關章節  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)  
  
## 請參閱  
 [使用程式碼剖析工具](../profiling/performance-explorer.md)