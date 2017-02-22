---
title: "DA0005：常見的 GC2 集合 | Microsoft Docs"
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
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0005：常見的 GC2 集合
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|RuleId|DA0005|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|.NET 記憶體|  
|Message|您的許多物件是在層代 2 記憶體回收時收集到的。|  
|訊息類型|警告|  
  
## 原因  
 大量 .NET 記憶體物件正在層代 2 記憶體回收中回收。  
  
## 規則描述  
 Microsoft .NET Common Language Runtime \(CLR\) 提供一套自動記憶體管理機制，會使用記憶體回收行程從應用程式不再使用的物件回收記憶體。  根據許多配置的存留期較短的假設，記憶體回收行程是層代導向。  例如，區域變數應該存留較短。  新建立的物件會從層代 0 \(Gen 0\) 開始，然後進入層代 1 \(當它們在記憶體回收行程之後存留下來時\)，最後轉換至層代 2 \(如果應用程式仍使用這些物件的話\)。  
  
 層代 0 中的物件較常回收而且通常非常有效率。  層代 1 中的物件較不常回收而且比較沒有效率。  最後，層代 2 中存留較久的物件應該更不常回收。  層代 2 回收 \(完全記憶體回收行程\) 也是成本最高昂的作業。  
  
 當發生比例過多的層代 2 記憶體回收時，便會引發這個規則。  如果過多相對短期存留的物件有通過層代 1，但之後無法在層代 2 完整集合中回收，記憶體管理的成本很可能會變得過多。  如需詳細資訊，請參閱 MSDN 網站上 Rico Mariani's Performance Tidbits 的[中間存留期危機](http://go.microsoft.com/fwlink/?LinkId=177835)張貼文章 \(英文\)。  
  
## 如何調查警告  
 檢閱[.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)報表，了解應用程式的記憶體配置模式。  使用 [物件存留期檢視](../profiling/object-lifetime-view.md) 可判斷程式的哪個資料物件可存留到層代 2 中，然後從該處回收。  使用 [配置檢視](../profiling/dotnet-memory-allocations-view.md)，判斷導致這些配置的執行路徑。  
  
 如需如何改善記憶體回收效能的詳細資訊，請參閱 Microsoft 網站上的[記憶體回收行程的基礎概念和效能提示](http://go.microsoft.com/fwlink/?LinkId=148226) \(英文\)。  如需有關自動記憶體回收額外負荷的詳細資訊，請參閱[大型物件堆積的面目](http://go.microsoft.com/fwlink/?LinkId=177836)。