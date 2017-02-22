---
title: "模組檢視 - 分析工具：取樣資料 | Microsoft Docs"
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
  - "模組檢視"
  - "取樣分析方法, 模組檢視"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 模組檢視 - 分析工具：取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取樣資料的 \[模組\] 檢視會顯示以程式碼剖析資料中取樣的模組分組的效能資料。  每個模組都是階層式樹狀結構的根項目。  模組中已取樣的函式會列在模組節點下面。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 如果函式在收集樣本時執行 \(也就是說函式位於呼叫堆疊的頂端\)，則執行的原始程式行和指令位址會列在函式節點下方。  由於原始程式行或指令執行時會收集程式行和指令指標的資料，因此程式行資料和指令資料的內含值和專有值固定相同。  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|模組、函式、行號或指令指標位址的名稱。|  
|**處理序 ID**|執行程式碼剖析期間的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含函式、程式行或指令指標的模組名稱。|  
|**模組路徑**|包含模組、函式、程式行或指令指標的模組路徑。|  
|**原始程式檔**|包含這個函式定義的原始程式檔。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**內含樣本**|-   對於函式而言，是此函式或此函式所呼叫之函式在其中執行的樣本數目，也就是包含此函式的呼叫堆疊樣本數目。<br />-   對於模組而言，是其中至少有一個模組中的函式正在執行的樣本數目。<br />-   對於程式行或指令而言，是此程式行或指令在其中執行的樣本數目。|  
|**內含樣本 %**|-   對於函式或模組而言，是在執行程式碼剖析期間，此函式或模組的內含樣本佔所有樣本的百分比。<br />-   對於程式行或指令而言，是程式碼剖析執行期間，此程式行或指令在其中執行之所有樣本的百分比。|  
|**專有樣本**|-   對於函式而言，是此函式直接在其中執行的呼叫堆疊樣本數目，也就是此函式在其中位於呼叫堆疊頂端的樣本數目。<br />-   對於模組而言，是模組中函式的專有樣本總和。<br />-   對於程式行或指令而言，是此程式行或指令在其中執行的樣本數目。|  
|**專有樣本 %**|-   對於函式或模組而言，是在執行程式碼剖析期間，此函式或模組的專有樣本佔所有樣本的百分比。<br />-   對於程式行或指令而言，是程式碼剖析執行期間，此程式行或指令在其中執行之所有樣本的百分比。|  
  
## 請參閱  
 [模組檢視 \- 取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [模組檢視 \- 檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [模組檢視](../profiling/modules-view-instrumentation-data.md)