---
title: "DA0504：進行程式碼剖析之處理序的最大工作集 (以位元組為單位) | Microsoft Docs"
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
  - "vs.performance.DA0504"
  - "vs.performance.504"
  - "vs.performance.rules.DA0504"
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0504：進行程式碼剖析之處理序的最大工作集 (以位元組為單位)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0504|  
|分類|資源管理|  
|程式碼剖析方法|全部|  
|Message|蒐集這項資訊僅供參考之用。  Process Working Set 計數器會測量您要分析的處理序的實際記憶體使用量。  回報的值就是在所有測量間隔中觀察到的最大值。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 規則描述  
 這個訊息回報處理序目前所使用的最大實體記憶體量 \(以位元組為單位\)。  處理序工作集代表處理序位址空間中目前位於實體記憶體內的頁面。  這個規則回報程式碼剖析處於作用中狀態時處理序工作集的最大值。  
  
 回報的值包含處理序所參考之共用記憶體區段的常駐頁面。  處理序所參考的共用 DLL 會包含在計入的共用記憶體區段中。  由於共用記憶體區段，處理序工作集的值可能比處理序已配置的虛擬記憶體量更高。  
  
 處理序工作集大小反映處理序目前正在使用的虛擬記憶體量。  它也會受到用來執行應用程式的實體記憶體 \(或 RAM\) 數量以及其他執行中處理序對該實體記憶體的爭用所影響。  如需處理序工作集的詳細資訊，請參閱MSDN 中的 Windows 記憶體管理文件 [工作集](http://go.microsoft.com/fwlink/?LinkId=177830) 。  
  
## 如何使用規則資料  
 規則會從 Windows 效能監視設備收集此度量資料，並回報僅供參考之用。  使用時可以比較程式之不同版本或組建間的效能，或了解應用程式在不同測試情節下的效能。  
  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至程式碼剖析資料的[標記檢視](../profiling/marks-view.md)。  尋找 **Process\\Working Set** 和 **Memory\\Pages\/sec** 計數器資料行。  然後，尋找 **Process\\Working Set** 的最大值，並將它和 **Memory\\Pages\/sec** 值相比較。  工作集最大值通常與分頁 IO 活動減少的間隔相關聯，特別是在電腦記憶體受限制時。