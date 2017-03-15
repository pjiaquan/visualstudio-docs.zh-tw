---
title: "DA0003：許多核心樣本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0003：許多核心樣本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0003|  
|分類|程式碼剖析工具使用|  
|程式碼剖析方法|取樣|  
|Message|您在核心模式中有高比例的樣本。  這可能表示有大量的 I\/O 活動或很高的內容切換率。  請考慮使用檢測模式重新分析您的應用程式。|  
|規則型別|資訊|  
  
## 原因  
 針對應用程式所收集的相當高比例的呼叫堆疊樣本是以核心模式執行。  請考慮使用不同的程式碼剖析方法對應用程式進行程式碼剖析。  
  
## 規則描述  
 在 Windows 中，程式碼可以在核心模式或使用者模式下執行。\(核心模式也稱為特殊權限模式\)。只有低階系統程式碼，例如裝置驅動程式，才能在核心模式下執行。  使用者模式應用程式可轉換至核心模式，以執行 I\/O 作業、等候執行緒或處理序同步處理基本型別，或執行系統呼叫。  
  
 針對花費大多數時間進行使用者模式下工作的應用程式進行程式碼剖析時，取樣會是最有效率的。  應用程式以核心模式執行時所收集到的範本數目，可以指出頻繁的 I\/O 作業，或是指出內容切換正在發生。  對於這些作業都無法使用取樣方法調查。  如果採用太多核心模式樣本，取樣資料可能不會包含足夠的使用者模式範例以具有統計上的意義。  
  
## 如何修正違規  
 考慮使用下列其中一個選項，再次對您的應用程式進行程式碼剖析：  
  
-   使用檢測方法進行程式碼剖析。  
  
-   增加取樣率以嘗試在使用者模式中收集更多樣本。