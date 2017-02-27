---
title: "如何：選擇收集方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具, 選擇收集方法"
  - "分析工具, 選擇收集方法"
  - "效能收集方法"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# 如何：選擇收集方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具支援三種收集效能資料的方法：取樣、檢測和並行。  您也可以使用取樣和檢測方法來收集 .NET 記憶體配置和存留期資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 您可以使用效能工作階段的 \[**方法**\] 屬性，為應用程式指定最適合的收集方法。  您可以從 \[效能精靈\]、\[效能總管\] 設定收集方法，或是從效能工作階段的屬性頁進行設定。  如果您是使用命令列工具，請參閱[從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)以取得詳細資訊。  
  
## 效能精靈  
  
#### 若要使用效能精靈選取收集方法  
  
-   您可以在精靈的第一頁選取下列其中一個選項：  
  
|選項|描述|  
|--------|--------|  
|**CPU 取樣**|收集應用程式統計資料，此資料對於初始分析以及分析 CPU 使用率問題很有用。|  
|**檢測**|收集詳細的執行時間資料，此資料對於焦點分析以及分析輸入\/輸出效能問題很有用。|  
|**.NET 記憶體配置**|使用取樣程式碼剖析方法，收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 記憶體配置資料。|  
|**並行**|收集數字資源爭用資料。|  
  
## 效能總管  
  
#### 若要使用效能總管選取收集方法  
  
1.  按一下 \[**效能總管**\] 工具列上 \[**方法** \] 下拉式清單旁邊的箭號。  
  
2.  按一下您想要使用的收集方法。  
  
## 效能工作階段屬性頁  
  
#### 若要使用效能工作階段屬性選取取樣或檢測方法  
  
1.  在 \[**效能總管**\] 中，選取效能工作階段。  
  
     效能工作階段檔案名稱的副檔名為 .psess。  
  
2.  以滑鼠右鍵按一下這個效能工作階段，然後按一下 \[**屬性**\]。  
  
3.  在 \[**屬性頁**\] 中，按一下 \[**一般**\]。  
  
4.  按一下您想要使用的收集方法。  
  
    -   如需收集取樣資料時其他可用選項的詳細資訊，請參閱[使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)。  
  
    -   如需收集取樣資料時其他可用選項的詳細資訊，請參閱[使用檢測收集計時詳細資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)。  
  
#### 若要使用效能工作階段屬性選取 .NET 記憶體資料收集  
  
1.  在 \[**效能總管**\] 中，選取效能工作階段。  
  
     效能工作階段檔案名稱的副檔名為 .psess。  
  
2.  以滑鼠右鍵按一下這個效能工作階段，然後按一下 \[**屬性**\]。  
  
3.  在 \[**屬性頁**\] 中，按一下 \[**一般**\]。  
  
4.  按一下 \[**取樣**\] 或 \[**檢測**\]。  
  
5.  按一下 \[**收集 .NET 物件配置資訊**\] 以收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 物件配置的大小和數目。  
  
6.  \(選擇性\) 按一下 \[**同時收集 .NET 物件存留期的資訊**\] 以收集用於回收物件記憶體之記憶體回收層代的相關資料。  
  
     如需收集 .NET 記憶體資料時其他可用選項的詳細資訊，請參閱[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)。  
  
#### 若要使用效能工作階段屬性選取並行資料收集  
  
1.  在 \[**效能總管**\] 中，以滑鼠右鍵按一下 \[效能工作階段\]，然後按一下 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 中，按一下 \[**一般**\]。  
  
3.  按一下 \[**並行**\]。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)