---
title: "DA0018：以處理序 Managed 記憶體限制執行的 32 位元應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.18"
  - "vs.performance.DA0018"
  - "vs.performance.rules.DA0018"
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0018：以處理序 Managed 記憶體限制執行的 32 位元應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0018|  
|分類|程式碼剖析工具使用|  
|程式碼剖析方法|取樣|  
|Message|Managed 記憶體配置即將接近 32 位元處理序的預設限制。  您的應用程式可能是 Memory\-bound。|  
|規則型別|警告|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 原因  
 在執行程式碼剖析期間所收集的系統資料指出，.NET Framework 記憶體堆積接近 32 位元處理序內允許的 Managed 堆積大小上限。  此大小上限為預設值。  它是根據可配置給私用位元組的處理序位址空間總數量。  回報的值就是進行程式碼剖析之處理序處於作用中狀態時觀察到的堆積最大值。  請考慮使用 .NET 記憶體程式碼剖析方法重新進行程式碼剖析，並且最佳化應用程式對 Managed 資源的使用。  
  
 當 Managed 堆積大小接近預設限制時，自動記憶體回收程序可能必須更常叫用。  這會增加記憶體管理的額外負荷。  
  
 此規則僅針對在 32 位元電腦上執行的 32 位元應用程式引發。  
  
## 規則描述  
 Microsoft .NET Common Language Run\-Time \(CLR\) 提供一套自動化的記憶體管理機制，它會使用記憶體回收行程從應用程式不再使用的物件中回收記憶體。  根據許多配置的存留期較短的假設，記憶體回收行程是層代導向。  例如，區域變數應該存留較短。  新建立的物件會從層代 0 \(Gen 0\) 開始，然後進入層代 1 \(當它們在記憶體回收行程之後存留下來時\)，最後轉換至層代 2 \(如果應用程式仍使用這些物件的話\)。  
  
 大於 85 KB 在大型物件堆積的 Managed 物件配置，所以它們比更小物件受到較少經常記憶體回收和壓縮限制。大型物件分開處理，因為假設，它們是詳細持續性，此外，因為混合持續性大型物件經常配置較小的物件可能會造成堆積的壞轉換分割。  
  
 當 Managed 堆積的總大小接近預設限制時，記憶體管理的額外負荷通常會增加，以致於開始影響應用程式的回應和延展性。  
  
## 如何調查警告  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至[標記](../profiling/marks-view.md)檢視。  尋找 **.NET CLR Memory\\\# Bytes in all Heaps** 和 **\# Total committed bytes** 資料行。  判斷是否有特定程式執行階段的 Managed 記憶體配置比其他階段更多。  將 **\# Bytes in all Heaps** 資料行的值與 **.NET CLR Memory\\\# of Gen 0 Collections**、**.NET CLR Memory\\\# of Gen 1 Collections** 和 **.NET CLR Memory\\\# of Gen 2 Collections** 資料行中所回報的記憶體回收比率相比較，判斷 Managed 記憶體配置模式是否影響記憶體回收比率。  
  
 在 .NET Framework 應用程式中，Common Language Runtime 將 Managed 堆積的總大小限制為略小於處理序位址空間私用區域部分大小上限的一半。  對於在 32 位元電腦上執行的 32 位元處理序，2 GB 代表處理序位址空間私用部分的上限。  當 Managed 堆積的總大小開始接近其預設限制時，管理記憶體的額外負荷可能會增加，而應用程式效能會降低。  
  
 如果非常高的 Managed 記憶體額外負荷構成問題，請考慮下列兩個選項之一：  
  
-   最佳化應用程式對 Managed 記憶體資源的使用  
  
     \-或\-  
  
-   採取步驟，解除 32 位元處理序虛擬記憶體大小上限的架構限制。  
  
 若要最佳化應用程式對 Managed 記憶體資源的使用，請在執行 .NET 記憶配置程式碼剖析中收集 Managed 記憶配置資料。  檢閱[.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)報表，了解應用程式的記憶體配置模式。  
  
 使用[物件存留期檢視](../profiling/object-lifetime-view.md)，判斷哪些程式物件在層代中存留，接著在此回收。  
  
 使用 [配置檢視](../profiling/dotnet-memory-allocations-view.md)，判斷導致這些配置的執行路徑。  
  
 如需如何改善記憶體回收效能的詳細資訊，請參閱 MSDN 網站上的 .NET Framework 技術文件：[記憶體回收行程的基礎概念和效能提示](http://go.microsoft.com/fwlink/?LinkId=177946) \(英文\)。  
  
 若要透過架構方式解除處理序位址空間私用部分大小的虛擬記憶體限制，請嘗試在 64 位元電腦上執行 32 位元處理序。在 64 位元電腦上的 32 位元處理序可以取得多達 4 GB 的私用虛擬記憶體。  
  
 在 64 位元電腦上執行的 64 位元處理序可以取得多達 8 TB 的虛擬記憶體。  考慮重新編譯應用程式，使其以原生 64 位元應用程式執行。  這個規則僅供參考，可能不需要更正動作。