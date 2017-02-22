---
title: "摘要檢視 - 程式碼剖析工具：.NET 記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "摘要檢視"
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 摘要檢視 - 程式碼剖析工具：.NET 記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[摘要\] 檢視顯示執行程式碼剖析時，配置最多記憶體的 .NET 函式和型別，以及建立最多次的型別的相關資訊。  如需詳細資訊，包括通知連結和報表清單的說明，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## 時間表圖形  
 \[摘要\] 檢視中的時間表圖形會顯示程式碼剖析期間，程式碼剖析的應用程式使用處理器 \(CPU\) 的情形。  您可以使用時間表圖形，將檢視篩選至選取的時間範圍。  如需詳細資訊，請參閱[如何：從摘要時間表篩選報表檢視](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 配置最多記憶體的函式  
 列出在執行程式碼剖析時，配置最多記憶體位元組數目的函式。  
  
|資料行|說明|  
|---------|--------|  
|**名稱**|函式的名稱。|  
|**位元組 %**|此函式或此函式所呼叫的子函式在執行程式碼剖析期間配置的所有已配置位元組的百分比。|  
  
## 配置最多記憶體的型別  
 列出在執行程式碼剖析時，得到最多記憶體位元組數目配置的型別。  
  
|資料行|說明|  
|---------|--------|  
|**名稱**|型別的名稱。|  
|**位元組 %**|在執行程式碼剖析期間，針對此型別配置的所有已配置位元組的百分比。|  
  
## 具有最多執行個體的型別  
 會列出在執行程式碼剖析期間建立最多次的型別。  
  
|資料行|說明|  
|---------|--------|  
|**名稱**|型別的名稱。|  
|**執行個體 %**|在執行程式碼剖析期間所建立，屬於此型別之執行個體的 .NET 物件總數的百分比。|  
  
## 請參閱  
 [摘要檢視](../profiling/summary-view-sampling-data.md)   
 [摘要檢視](../profiling/summary-view-instrumentation-data.md)