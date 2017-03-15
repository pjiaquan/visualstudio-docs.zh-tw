---
title: "DA0021：高比率的 Gen 1 記憶體回收 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0021：高比率的 Gen 1 記憶體回收
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0021|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|全部|  
|Message|發生相當高比率的 Gen 1 記憶體回收。  如果在設計上程式的資料結構需要配置並且保存較長的時間，那麼這種情況通常並不構成問題。  不過，如果這並非預期的行為，那麼您的應用程式可能正在固定物件。  如果您不確定，請收集 .NET 記憶體配置資料和物件存留期資訊，了解應用程式所使用的記憶體配置模式。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 原因  
 程式碼剖析期間收集的系統效能資料指出，相較於層代 0 資料收集，層代 1 記憶體回收中回收相當高比例的 .NET Framework 物件記憶體。  
  
## 規則描述  
 Microsoft .NET Common Language Run\-Time \(CLR\) 提供一套自動化的記憶體管理機制，它會使用記憶體回收行程從應用程式不再使用的物件中回收記憶體。  根據許多配置的存留期較短的假設，記憶體回收行程是層代導向。  例如，區域變數應該存留較短。  新建立的物件會從層代 0 \(Gen 0\) 開始，然後進入層代 1 \(當它們在記憶體回收行程之後存留下來時\)，最後轉換至層代 2 \(如果應用程式仍使用這些物件的話\)。  
  
 層代 0 中的物件較常回收而且通常非常有效率。  層代 1 中的物件較不常回收而且比較沒有效率。  最後，層代 2 中存留較久的物件應該更不常回收。  層代 2 回收 \(完全記憶體回收行程\) 也是成本最高昂的作業。  
  
 當發生比例過多的層代 1 記憶體回收時，便會引發這個規則。  如果太多存留相當短暫的物件在層代 0 記憶體回收中未被回收，但仍然能夠在層代 1 記憶體回收中回收，記憶體管理成本可能變得過高。  如需詳細資訊，請參閱 MSDN 網站上 Rico Mariani's Performance Tidbits 的[中間存留期危機](http://go.microsoft.com/fwlink/?LinkId=177835)張貼文章 \(英文\)。  
  
## 如何調查警告  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至程式碼剖析資料的[標記檢視](../profiling/marks-view.md)。  尋找 **.NET CLR Memory\\\# of Gen 0 Collections** 和 **.NET CLR Memory\\\# of Gen 1 Collections** 資料行。  判斷是否有特定程式執行階段的記憶體回收較為頻繁。  將這些值與 **% Time in GC** 資料行相比較，判斷 Managed 記憶體配置模式是否導致過多的記憶體管理額外負荷。  
  
 若要了解應用程式的 Managed 記憶體使用模式，請執行 .NET 記憶體配置設定檔以重新進行程式碼剖析，並要求 \[物件存留期\] 度量。  
  
 如需如何改善記憶體回收效能的詳細資訊，請參閱 Microsoft 網站上的[記憶體回收行程的基礎概念和效能提示](http://go.microsoft.com/fwlink/?LinkId=148226) \(英文\)。  如需有關自動記憶體回收額外負荷的詳細資訊，請參閱[大型物件堆積的面目](http://go.microsoft.com/fwlink/?LinkId=177836)。