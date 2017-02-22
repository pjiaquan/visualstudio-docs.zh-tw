---
title: "DA0010：GetHashCode 高度耗費資源 | Microsoft Docs"
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
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0010：GetHashCode 高度耗費資源
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0010|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|取樣<br /><br /> .NET 記憶體|  
|訊息|GetHashCode 函式應該不耗費資源、不配置任何記憶體。  請盡可能降低雜湊碼函式的複雜度。|  
|訊息類型|警告|  
  
## 原因  
 對型別之 GetHashCode 方法的呼叫佔程式碼剖析資料顯著的比例，或方法配置記憶體。  
  
## 規則描述  
 雜湊是可以快速找到大型集合中特定項目的技術。  因為雜湊資料表可以非常龐大，而且必須支援非常高的存取速率，雜湊資料表應該極有效率。   這項需求的涵意，是在 .NET Framework 中的 GetHashCode 方法不應該配置記憶體。  配置記憶體會增加記憶體回收行程的負荷，而且公開的方法如果因為配置要求而需要執行記憶體回收，也可能會造成延遲。  
  
## 如何修正違規  
 請降低方法的複雜度。