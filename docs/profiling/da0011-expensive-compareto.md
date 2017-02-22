---
title: "DA0011：CompareTo 高度耗費資源 | Microsoft Docs"
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
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0011：CompareTo 高度耗費資源
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0011|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|取樣<br /><br /> .NET 記憶體|  
|訊息|CompareTo 函式應該不耗費資源、不配置任何記憶體。  請盡可能降低 compareTo 函式的複雜度。|  
|規則型別|警告|  
  
## 原因  
 型別的 CompareTo 方法高度耗費資源或會配置記憶體。  
  
## 規則描述  
 CompareTo 方法應足夠且不應配置記憶體。  
  
## 如何修正違規  
 降低 CompareTo 方法的複雜度。