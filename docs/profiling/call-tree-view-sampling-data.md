---
title: "呼叫樹狀圖檢視 - 程式碼剖析工具：取樣資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取樣分析方法，呼叫樹狀圖檢視"
  - "呼叫樹狀圖檢視"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 呼叫樹狀圖檢視 - 程式碼剖析工具：取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[呼叫樹狀圖\] 檢視會顯示在被剖析的應用程式中可測定的函式執行路徑。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 樹狀圖的根是應用程式或元件的進入點。  每個函式節點會列出它呼叫的所有函式以及這些函式呼叫的相關效能資料。  
  
 呼叫樹狀圖檢視中的值適用於呼叫樹狀圖中父函式所呼叫的函式執行個體。  百分比值是透過比較函式執行個體值和執行程式碼剖析期間樣本總數而算出。  
  
## 反白顯示執行的最忙碌路徑  
 \[呼叫樹狀圖\] 檢視可以展開和反白顯示最常取樣之處理序或函式的執行路徑。  若要顯示活動最頻繁的路徑，請以滑鼠右鍵按一下該處理序或函式，然後按一下 \[**展開最忙碌路徑**\]。  
  
## 設定呼叫樹狀圖根節點  
 程式碼剖析執行中的每個處理序都會顯示成一個根節點。  若要設定 \[呼叫樹狀圖\] 檢視的開始節點，請以滑鼠右鍵按一下要設定為開始節點的節點，然後選取 \[**設定根目錄**\]。  
  
 設定根節點時，除了選取之節點的樹狀子目錄以外，請從檢視中排除所有其他的項目。  若要將根節點重設為原始節點，請以滑鼠右鍵按一下 \[呼叫樹狀圖\] 檢視視窗，然後選取 \[**重設根目錄**\]。  
  
|資料行|描述|  
|---------|--------|  
|**處理序 ID**|執行程式碼剖析期間的處理序 ID \(PID\)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**原始程式檔**|包含這個函式定義的原始程式檔。|  
|**函式名稱**|函式的完整名稱。|  
|**函式行號**|在原始程式檔中這個函式的開頭行號。|  
|**函式位址**|函式的位址。|  
|**層級**|呼叫樹狀圖中此函式的深度。  只存在於 [VSPerfReport](../profiling/vsperfreport.md) 命令列報告中。|  
|**專有樣本**|呼叫樹狀圖中的父函式呼叫此函式時，在此函式中收集到的樣本數目。  此數目不包括此函式所呼叫的函式中已收集的樣本。|  
|**專有樣本 %**|在呼叫樹狀圖中的父函式呼叫此函式時，此函式的專有樣本佔執行程式碼剖析期間所有樣本的百分比。|  
|**內含樣本**|呼叫樹狀圖中的父函式呼叫此函式時，在此函式中收集到的樣本數目。  此數目包括此函式所呼叫的函式中已收集的樣本。|  
|**內含樣本 %**|在呼叫樹狀圖中的父函式呼叫此函式時，此函式的內含樣本佔執行程式碼剖析期間所有樣本的百分比。|  
  
## 請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [呼叫樹狀圖檢視 \- 取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [呼叫樹狀圖檢視 \- 檢測](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [呼叫樹狀圖檢視](../profiling/call-tree-view-instrumentation-data.md)