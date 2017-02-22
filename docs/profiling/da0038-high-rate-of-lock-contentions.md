---
title: "DA0038：鎖定爭用的比率很高 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.38"
  - "vs.performance.rules.DA0038"
  - "vs.performance.DA0038"
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0038：鎖定爭用的比率很高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0038|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|取樣<br /><br /> 檢測<br /><br /> .NET 記憶體|  
|Message|發生高比率的 .NET 鎖定爭用。  請執行並行分析來探查鎖定爭用的原因。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 25 個範本才能觸發此規則。  
  
## 原因  
 隨程式碼剖析資料一起收集的系統效能資料指出，在應用程式執行期間發生相當高比率的鎖定爭用。  請考慮使用並行程式碼剖析方法重新進行程式碼剖析，找出爭用原因。  
  
## 規則描述  
 鎖定是用來保護每次只能由多執行緒應用程式的一個執行緒循序執行的關鍵程式碼區段。  Microsoft .NET Common Language Runtime \(CLR\) 提供一組完整的同步處理和鎖定基本型別。  例如，C\# 語言支援 lock 陳述式 \(在 Visual Basic 中則為 SyncLock\)。  Managed 應用程式可以呼叫 System.Threading 命名空間中的 Monitor.Enter 和 Monitor.Exit 方法，直接取得鎖定後再釋放。  .NET Framework 支援其他同步處理和鎖定基本型別，包括支援 Mutexes、ReaderWriterLocks 和 Semaphores 的類別。  如需詳細資訊，請參閱 MSDN 網站上《.NET Framework 開發人員手冊》中的[同步處理原始物件概觀](http://go.microsoft.com/fwlink/?LinkId=177867)。  .NET Framework 類別本身是在 Windows 作業系統之內建低階同步處理服務的上層。  這些服務包含關鍵區段物件以及許多不同的 Wait 和事件訊號函式。  如需詳細資訊，請參閱 Win32 [同步處理](http://go.microsoft.com/fwlink/?LinkId=177869) 和 COM 程式開發 \> 章節的 MSDN Library  
  
 在用於同步處理和鎖定的 .NET Framework 類別和原生 Windows 物件之下，是必須透過連鎖作業變更的共用記憶體位置。  連鎖作業使用硬體特定指令，在共用記憶體位置上操作，以透過不可部分完成的作業來變更其狀態。  不可部分完成的作業在電腦上的所有處理器之間會保證一致性。  Locks 和 WaitHandles 是在設定或重設時自動使用連鎖作業的 .NET 物件。  您的應用程式中可能有其他共用記憶體資料結構也需要使用連鎖作業，才能透過安全執行緒方式來更新。  如需詳細資訊，請參閱在 MSND Library 之 .NET Framework 組件上的 [連鎖作業](http://go.microsoft.com/fwlink/?LinkId=177870) 。  
  
 同步處理和鎖定是用來確保多執行緒應用程式能正確執行的機制。  多執行緒應用程式的每個執行緒是由作業系統分別排程的獨立執行單元。  當嘗試取得鎖定的執行緒因為另一個執行緒持有該鎖定而延遲時，便會發生鎖定爭用。  
  
 鎖定常為巢狀。  當執行關鍵區段的執行緒執行一個需要另一個鎖定的函式時，便會發生巢狀。  部分數量的鎖定巢狀是不可避免的。  您的關鍵區段可能呼叫一個依賴鎖定以確保其為安全執行緒的 .NET Framework 方法。  應用程式中的某個關鍵區段呼叫一個也透過不同鎖定控制代碼來鎖定的 Framework 方法，就會導致巢狀鎖定。  巢狀鎖定狀況可能造成極難以解決及修正的效能問題。  
  
 在程式碼剖析執行期間取得的度量指出非常高比率的鎖定爭用時，會引發這個規則。  鎖定爭用會使等候鎖定的執行緒延遲執行。  即使在低階硬體上所執行單元測試或負載測試中的相當少量鎖定爭用，都應該進行調查。  
  
> [!NOTE]
>  當程式碼剖析資料中所報告的鎖定爭用比率過高時，則會引發 [DA0039：鎖定爭用的比率非常高](../profiling/da0039-very-high-rate-of-lock-contentions.md)警告訊息，而不是這個資訊訊息。  
  
## 如何調查警告  
 按兩下訊息，巡覽至程式碼剖析資料的[標記](../profiling/marks-view.md)檢視。尋找 **.NET CLR LocksAndThreads\\Contention Rate \/ sec** 資料行。  判斷是否有特定程式執行階段的鎖定爭用比其他階段更多。  
  
 這個規則只有在不是使用並行程式碼剖析方法時才會引發。  並行程式碼剖析方法是用來診斷應用程式中與鎖定爭用相關之效能問題的最佳工具。  收集並行程式碼剖析資料，可以了解應用程式的鎖定行為，  包括了解哪些鎖定被大量爭用、執行緒執行時間因等候爭用鎖定而延遲多久，以及哪些特定程式碼涉及其中。  並行程式碼剖析會收集所有鎖定爭用的資料，包括原生 Windows 機能、.NET Framework 類別，以及應用程式所參考之任何其他協力廠商程式庫的鎖定行為。  如需從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 執行並行程式碼剖析的詳細資訊，請參閱[收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)。  如需如何從命令列執行並行程式碼剖析的資訊連結，請參閱[從命令列使用程式碼剖析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)的**Using the Concurrency Method to Collect Resource Contention and Thread Activity Data**一節。