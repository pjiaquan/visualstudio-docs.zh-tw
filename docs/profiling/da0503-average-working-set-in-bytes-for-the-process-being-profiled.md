---
title: "DA0503：進行程式碼剖析之處理序的平均工作集 (以位元組為單位) | Microsoft Docs"
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
  - "vs.performance.503"
  - "vs.performance.DA0503"
  - "vs.performance.rules.DA0503"
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0503：進行程式碼剖析之處理序的平均工作集 (以位元組為單位)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0503|  
|分類|資源監視|  
|程式碼剖析方法|全部|  
|Message|蒐集這項資訊僅供參考之用。  Process Working Set 計數器會測量您要分析的處理序的實際記憶體使用量。  所報告的值是在所有測量間隔中計算出的平均值。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 規則描述  
 這個訊息回報處理序目前所使用的平均實體記憶體量 \(工作集，以位元組為單位\)。  處理序工作集代表處理序位址空間中目前位於實體記憶體內的頁面。  
  
 回報的值包含處理序所參考之共用記憶體區段的常駐頁面。  處理序所參考的共用 DLL 會包含在計入的共用記憶體區段中。  由於共用記憶體區段，處理序工作集的值可能比處理序已配置的虛擬記憶體量更高。  
  
 回報的值就是進行程式碼剖析之處理序處於作用中狀態的所有測量間隔的平均值。  
  
 處理序工作集大小反映處理序目前正在使用的虛擬記憶體量。  它也會受到用來執行應用程式的實體記憶體 \(或 RAM\) 數量以及其他執行中處理序對該實體記憶體的爭用所影響。  如果實體記憶體受限制，隨著作業系統定期修剪處理序工作集中的非使用中頁面，嘗試在使用中處理序之間平衡記憶體使用量，處理序工作集的值易於大幅變更。  
  
 如需處理序工作集的詳細資訊，請參閱MSDN 中的 Windows 記憶體管理文件 [工作集](http://go.microsoft.com/fwlink/?LinkId=177830) 。  
  
## 如何使用規則資料  
 使用規則值可以比較程式之不同版本或組建間的效能，或了解應用程式在不同程式碼剖析情節下的效能。  
  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至程式碼剖析資料的[標記檢視](../profiling/marks-view.md)。  尋找 **Process\\Working Set** 和 **Memory\\Pages\/sec** 資料行。  比較兩個資料行，判斷是否有特定程式執行階段看起來與增加的分頁 IO 活動相關聯。