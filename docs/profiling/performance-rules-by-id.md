---
title: "依 ID 排序的效能規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a1c934c-4798-4df9-a8ef-eb17ef06b6a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 依 ID 排序的效能規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|警告|說明|  
|--------|--------|  
|[DA0001：使用 StringBuilder 進行串連](../Topic/DA0001:%20Use%20StringBuilder%20for%20concatenations.md)|呼叫 System.String.Concat 佔用程式碼剖析資料相當大的百分比。  請考慮使用 <xref:System.Text.StringBuilder> 類別從多個區段建構字串。|  
|[DA0002：遺漏 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|程式碼剖析工具在執行程式碼剖析期間找不到 VSPerfCorProf.dll。  使用命令列工具收集分析工具資料，但未使用 VSPerfCLREnv.cmd 工具初始化必要的環境變數時，會發生這個警告。|  
|[DA0003：許多核心樣本](../profiling/da0003-many-kernel-samples.md)|針對應用程式所收集的相當高比例的呼叫堆疊樣本是以核心模式執行。  請考慮使用不同的程式碼剖析方法，為應用程式進行程式碼剖析。|  
|[DA0004：處理器使用率高](../profiling/da0004-high-processor-usage.md)|透過檢測方法所收集的程式碼剖析資料中，處理器 \(CPU\) 使用率相當高。  對 CPU 繫結的應用程式進行程式碼剖析時，請考慮使用取樣分析方法。|  
|[DA0005：常見的 GC2 集合](../profiling/da0005-frequent-gc2-collections.md)|大量 .NET 記憶體物件正在層代 2 記憶體回收中回收。|  
|[DA0006：覆寫實值類型的 Equals\(\)](../profiling/da0006-override-equals-parens-for-value-types.md)|對 Equals 方法或公用實值型別之等號比較運算子的呼叫佔程式碼剖析資料顯著的比例。  請考慮實作更有效率的方法。|  
|[DA0007：避免使用例外狀況進行控制流程](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|程式碼剖析資料中呼叫了高比率的 .NET Framework 例外狀況處理常式。  請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數目。|  
|[DA0008：收集的樣本少](../profiling/da0008-few-samples-collected.md)|執行程式碼剖析期間僅收集少數樣本。  請考慮延長執行時間或使用較快的取樣率，以取得更重要的結果。|  
|[DA0009: High % time in JIT](http://msdn.microsoft.com/zh-tw/b60c1767-515c-41d9-81c2-c70d0b7024fd)|在 Just In Time \(JIT\) 編譯器中花費了相當程度的應用程式執行時間。|  
|[DA0010：GetHashCode 高度耗費資源](../profiling/da0010-expensive-gethashcode.md)|對型別之 GetHashCode 方法的呼叫佔程式碼剖析資料顯著的比例，或方法配置記憶體。|  
|[DA0011：CompareTo 高度耗費資源](../profiling/da0011-expensive-compareto.md)|型別的 CompareTo 方法高度耗費資源或會配置記憶體。|  
|[DA0012：大量的反射](../Topic/DA0012:%20Significant%20amount%20of%20Reflection.md)|對 System.Reflection 方法 \(例如 InvokeMember 和 GetMember\) 或對 Type 方法 \(例如 MemberInvoke\) 的呼叫佔程式碼剖析資料顯著的比例。  可能的話，請考慮用相依組件之方法的早期繫結來取代這些方法。|  
|[DA0013：String.Split 或 String.Substring 的用量高](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|呼叫 System.String.Split or System.String.Substring 佔用程式碼剖析資料相當大的部分。  如果您要測試字串中是否存在子字串，請考慮使用 System.String.IndexOf 或 System.String.IndexOfAny。|  
|[DA0014：極高比率的使用中記憶體分頁到磁碟](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|執行程式碼剖析時所收集的系統效能資料指出，在整個程式碼剖析執行期間發生非常高比率的作用中記憶體對磁碟的來回分頁。  這個層級的分頁比率通常會影響應用程式的效能和回應。  請考慮修訂演算法來降低記憶體配置。  您可能也必須考慮應用程式的記憶體需求。執行重新設定檔在具有更多記憶體的電腦。|  
|[DA0017：作用中的記憶體分頁至磁碟的比率很高](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|執行程式碼剖析時所收集的系統效能資料指出，在整個程式碼剖析執行期間發生高比率的作用中記憶體對磁碟的來回分頁。  這個層級的分頁比率通常會影響應用程式的效能和回應。  請考慮修訂演算法來降低記憶體配置。  您可能也必須考慮應用程式的記憶體需求。執行重新設定檔在具有更多記憶體的電腦。|  
|[DA0018：以處理序 Managed 記憶體限制執行的 32 位元應用程式](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|在執行程式碼剖析期間所收集的系統資料指出，.NET Framework 記憶體堆積接近 32 位元處理序內允許的 Managed 堆積大小上限。  回報的值就是進行程式碼剖析之處理序處於作用中狀態時觀察到的堆積最大值。  請考慮最佳化應用程式對 Managed 資源的使用。|  
|[DA0021：高比率的 Gen 1 記憶體回收](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|程式碼剖析期間收集的系統效能資料指出，相較於層代 0 資料收集，層代 1 記憶體回收中回收相當高比例的 .NET Framework 物件記憶體。|  
|[DA0022：高比率的 Gen 2 記憶體回收](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|程式碼剖析期間收集的系統效能資料指出，相較於層代 0 和層代 1 記憶體回收，層代 2 記憶體回收中回收相當高比例的 .NET Framework 物件記憶體。|  
|[DA0023：高 GC CPU 時間](../profiling/da0023-high-gc-cpu-time.md)|程式碼剖析期間收集的系統效能資料指出，相較於應用程式處理總時間，記憶體回收所花費的時間量相當高。|  
|[DA0024：過多 GC CPU 時間](../profiling/da0024-excessive-gc-cpu-time.md)|程式碼剖析期間收集的系統效能資料指出，相較於應用程式處理總時間，記憶體回收所花費的時間量過高。|  
|[DA0026：過多核心 CPU 時間處理](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|以核心模式執行的 CPU 時間比例超過使用者模式所花的時間量。  請考慮重新進行程式碼剖析並取樣系統呼叫 \(syscalls\) 數目，以判斷造成高核心模式執行時間的原因。|  
|[DA0029：不支援的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|您嘗試對使用 .NET Framework 1.1 版的應用程式進行程式碼剖析，但程式碼剖析工具不支援此版本。|  
|[DA0030：蒐集資料庫專案的階層互動度量](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|對 <xref:System.Data> 方法的呼叫佔程式碼剖析資料顯著的比例，而且您尚未在程式碼剖析執行時收集階層互動資料。  請考慮重新進行程式碼剖析並加入階層互動資料。|  
|[DA0038：鎖定爭用的比率很高](../profiling/da0038-high-rate-of-lock-contentions.md)|隨程式碼剖析資料一起收集的系統效能資料指出，在應用程式執行期間發生相當高比率的鎖定爭用。  請考慮使用並行程式碼剖析方法重新進行程式碼剖析，找出爭用原因。|  
|[DA0039：鎖定爭用的比率非常高](../profiling/da0039-very-high-rate-of-lock-contentions.md)|隨程式碼剖析資料一起收集的系統效能資料指出，在應用程式執行期間發生比率過高的鎖定爭用。  請考慮使用並行程式碼剖析方法重新進行程式碼剖析，找出爭用原因。|  
|[DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|這個訊息回報處理器忙於執行應用程式指令的時間百分比。  回報的值就是進行程式碼剖析之處理序處於作用中狀態的所有測量間隔的平均值。  在具有一個以上處理器的電腦上，百分比值可能大於 100%。|  
|[DA0502：進行程式碼剖析之處理序所需的最大 CPU 使用量](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|這個訊息回報處理器忙於執行應用程式指令的最大時間百分比。  回報的值是要程式碼剖析之處理序處於作用中狀態的所有測量間隔所回報的最大值。  在具有一個以上處理器的電腦上，百分比可能大於 100%。|  
|[DA0503：進行程式碼剖析之處理序的平均工作集 \(以位元組為單位\)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|這個訊息回報處理序目前所使用的平均實體記憶體量 \(工作集，以位元組為單位\)。  處理序工作集代表處理序位址空間中目前位於實體記憶體內的頁面。|  
|[DA0504：進行程式碼剖析之處理序的最大工作集 \(以位元組為單位\)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|這個訊息回報處理序目前所使用的最大實體記憶體量 \(以位元組為單位\)。  處理序工作集代表處理序位址空間中目前位於實體記憶體內的頁面。  這個規則回報程式碼剖析處於作用中狀態時處理序工作集的最大值。|  
|[DA0505：為進行程式碼剖析的處理序所配置的平均私用位元組](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|這個訊息回報處理序目前已配置的平均虛擬記憶體量 \(私用位元組，以位元組為單位\)。  私用位元組代表由處理序所配置而且只能供在處理序內部執行之執行緒存取的虛擬記憶體位置。|  
|[DA0506：為進行程式碼剖析的處理序所配置的最大私用位元組](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|這個訊息回報處理序目前已配置的最大虛擬記憶體量 \(私用位元組，以位元組為單位\)。  私用位元組代表由處理序所配置而且只能供在處理序內部執行之執行緒存取的虛擬記憶體位置。|