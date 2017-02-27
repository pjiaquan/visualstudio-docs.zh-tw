---
title: "模組檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.modules"
helpviewer_keywords: 
  - "模組檢視"
  - "程式碼剖析工具報告, 模組檢視"
  - "程式碼剖析工具, 模組檢視"
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# 模組檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[模組\] 檢視會列出程式碼剖析資料的模組。  每個模組都是階層式樹狀結構的根節點。  模組中已經進行過程式碼剖析的函式會列在模組節點下面，  如果程式碼剖析資料已經利用取樣方法收集，那麼程式行資訊列在函式節點下方，而指令指標資料則列在程式行節點下面。  
  
 請展開或摺疊模組名稱來顯示或關閉模組效能資料的檢視。  
  
 若要新增或移除資料行，請以滑鼠右鍵按一下報告視窗，然後選取 \[**新增\/移除資料行**\]。  您可以按一下資料行名稱來排序資料。  如需詳細資訊，請參閱[如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
 \[模組\] 檢視中會出現的資料行，取決於收集資料時使用的程式碼剖析方法 \(取樣或檢測\)，以及在執行程式碼剖析期間是否有收集 .NET 記憶體資料。  
  
## 請參閱  
 [模組檢視](../profiling/modules-view-sampling-data.md)   
 [模組檢視](../profiling/modules-view-instrumentation-data.md)   
 [模組檢視 \- 檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [模組檢視 \- 取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [模組檢視](../profiling/modules-view-contention-data.md)