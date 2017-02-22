---
title: "呼叫樹狀圖檢視 | Microsoft Docs"
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
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "呼叫樹狀圖檢視"
  - "效能報告, 呼叫樹狀圖檢視"
  - "程式碼剖析工具報告, 呼叫樹狀圖檢視"
  - "程式碼剖析工具, 呼叫樹狀圖檢視"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 呼叫樹狀圖檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[呼叫樹狀圖\] 檢視會顯示在被剖析的應用程式中可測定的函式執行路徑。  樹狀圖的根是應用程式或元件的進入點。  每個函式節點會列出它呼叫的所有函式以及這些函式呼叫的相關效能資料。  
  
 \[呼叫樹狀圖\] 檢視也可以展開和反白顯示消耗最多時間或最常取樣之函式的執行路徑。  若要顯示效能成本最高的路徑，請以滑鼠右鍵按一下該型別或函式，然後按 \[**展開最忙碌路徑**\]。  
  
 程式碼剖析執行中的每個處理序都會顯示成一個根節點。  您可以在要設成開始節點的節點上，以滑鼠右鍵按一下，然後選取 \[**設定根目錄**\]，以設定 \[呼叫樹狀圖\] 檢視的開始節點。  
  
 設定根節點時，除了選取之節點的樹狀子目錄以外，請從檢視中排除所有其他的項目。  您可以將根節點重設回先前檢視的節點。  請在 \[呼叫樹狀圖檢視\] 視窗中按一下滑鼠右鍵，然後選取 \[**重設根目錄**\]。  
  
 您可以自訂 \[呼叫樹狀圖\] 檢視，以加入或移除資料行。  請以滑鼠右鍵按一下**資料行名稱標題列**，然後選取 \[**新增\/移除資料行**\]。  
  
 您可以透過限制顯示的資料量，設定 \[呼叫樹狀圖\] 檢視以減少雜訊。  使用雜訊削減時，檢視中的效能問題將更為顯著。  當您能夠輕易區別效能問題時，分析也將更加容易。  如需詳細資訊，請參閱[如何：在報表檢視中設定減少雜訊](../profiling/how-to-configure-noise-reduction-in-report-views.md)。  
  
> [!NOTE]
>  如果您已設定要在啟用雜訊削減時顯示警告，報告中將會顯示資訊列。  
  
 如需 \[呼叫樹狀圖\] 檢視中資料行之定義的詳細資訊，請參閱下列內容：  
  
 [呼叫樹狀圖檢視](../profiling/call-tree-view-sampling-data.md)  
  
 [呼叫樹狀圖檢視](../profiling/call-tree-view-instrumentation-data.md)  
  
 [呼叫樹狀圖檢視 \- 取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [呼叫樹狀圖檢視](../profiling/call-tree-view-contention-data.md)  
  
## 請參閱  
 [程式碼剖析工具報表檢視](../profiling/performance-report-views.md)   
 [認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)   
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)