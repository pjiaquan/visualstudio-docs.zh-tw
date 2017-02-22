---
title: "DA0502：進行程式碼剖析之處理序所需的最大 CPU 使用量 | Microsoft Docs"
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
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0502：進行程式碼剖析之處理序所需的最大 CPU 使用量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0502|  
|分類|資源監視|  
|程式碼剖析方法|全部|  
|訊息|此規則僅供參考。  Process\(\)\\% Processor Time 計數器會測量您要程式碼剖析的處理序的 CPU 消耗。  所報告的值是在所有測量間隔觀察到的最大值。|  
|規則型別|告知性|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 規則描述  
 這個訊息回報處理器忙於執行應用程式指令的最大時間百分比。  回報的值是要程式碼剖析之處理序處於作用中狀態的所有測量間隔所回報的最大值。  在具有一個以上處理器的電腦上，百分比可能大於 100%。  
  
## 如何使用規則資料  
 使用規則值可以比較程式之不同版本或組建間的效能，或了解應用程式在不同程式碼剖析情節下的效能。