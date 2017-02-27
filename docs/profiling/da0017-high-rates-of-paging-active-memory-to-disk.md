---
title: "DA0017：作用中的記憶體分頁至磁碟的比率很高 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.17"
  - "vs.performance.rules.DA0017"
  - "vs.performance.DA0017"
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0017：作用中的記憶體分頁至磁碟的比率很高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0017|  
|分類|記憶體和分頁|  
|程式碼剖析方法|全部|  
|訊息|發生高比率的使用中記憶體分頁到磁碟。  您的應用程式可能是 Memory\-bound。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 原因  
 執行程式碼剖析時所收集的系統效能資料指出，在整個程式碼剖析執行期間發生高比率的作用中記憶體對磁碟的來回分頁。  這個層級的分頁比率通常會影響應用程式的效能和回應。  請考慮修訂演算法來降低記憶體配置。  您可能也必須考慮應用程式的記憶體需求。  
  
## 規則描述  
  
> [!NOTE]
>  當作用中記憶體的分頁層級達到相當多量時，會引發這個資訊規則。  當發生非常高的分頁層級時，則會引發警告規則 [DA0014：極高比率的使用中記憶體分頁到磁碟](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)。  
  
 分頁至磁碟過多，可能是因為實體記憶體不足所造成。  如果分頁作業在分頁檔案所在的實體磁碟上佔主要使用率，可能會使相同磁碟上的其他應用程式導向磁碟作業執行速度變慢。  
  
 頁面通常是在大量分頁作業中從磁碟讀取或寫入磁碟。  例如，Pages Output\/sec 的數字通常比 Page Writes\/sec 的數字大得多。  這是因為 Pages Output\/sec 也包含系統檔案快取中已變更的資料頁面。  不過，哪個處理序直接導致分頁或其原因並不一定容易判斷。  
  
## 如何修正違規  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至[標記](../profiling/marks-view.md)檢視。  尋找 **Memory\\Pages\/sec** 資料行。  判斷是否有特定程式執行階段的分頁 IO 活動比其他階段更多。  
  
 如果您在負載測試情節中收集 ASP.NET 應用程式的程式碼剖析資料，請嘗試在設定有更多實體記憶體 \(或 RAM\) 的電腦上重新執行負載測試。  
  
 請考慮修改演算法並避免大量耗用記憶體的 API \(例如 String.Concat 和 String.Substring\)，以減少記憶體配置。