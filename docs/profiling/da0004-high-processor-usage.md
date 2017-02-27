---
title: "DA0004：處理器使用率高 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0004：處理器使用率高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0004|  
|分類|程式碼剖析工具使用|  
|程式碼剖析方法|檢測<br /><br /> 取樣|  
|訊息|處理器使用率始終高於 75%。  請考慮針對 CPU\-bound 應用程式使用「取樣」模式。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 原因  
 透過檢測方法所收集的程式碼剖析資料中，處理器 \(CPU\) 使用率相當高。  對 CPU 繫結的應用程式進行程式碼剖析時，請考慮使用取樣分析方法。  
  
## 規則描述  
 在此程式碼剖析的執行期間，單一或多處理器都會一致地非常忙碌。  高 CPU 使用率可指出 CPU 繫結應用程式。  已檢測的設定檔通常不是調查 CPU 使用情況的最有效方式。  針對花費大多數時間執行處理器之指令的應用程式進行程式碼剖析時，取樣通常都會較有效率。  
  
## 如何修正違規  
 請考慮使用取樣方法再次對應用程式進行程式碼剖析，而非使用檢測方法，除非您需要函式計時，或是對輸入\/輸出比處理器瓶頸更有興趣了解。