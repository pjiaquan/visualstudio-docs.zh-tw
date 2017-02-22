---
title: "設定程式碼剖析工具的效能工作階段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "一般工作，效能"
  - "一般工作，程式碼剖析工具"
  - "程式碼剖析工具，一般工作"
  - "效能，收集資料"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 設定程式碼剖析工具的效能工作階段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具收集許多應用程式類型的各類效能資料。  本章節說明如何使用效能工作階段的 \[**效能精靈**\] 和屬性以及目標二進位檔，設定程式碼剖析工具以收集所需的資料。  程式碼剖析工具組態屬性還可用於控制在進行程式碼剖析期間收集的資料量。  如需詳細資訊，請參閱[控制資料收集](../profiling/controlling-data-collection.md)。  
  
> [!NOTE]
>  在許多情況下，使用 \[效能精靈\] 的預設屬性來收集程式碼剖析資料都很有效率。  如需詳細資訊，請參閱[效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)與[使用者入門](../profiling/getting-started-with-performance-tools.md)。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**設定基本的程式碼剖析選項**：您應該設定 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 使用 Microsoft 符號伺服器。  這可以確保您能存取目前 Windows 和其他 Microsoft 應用程式版本的符號，例如函式和參數名稱。  您也可以在程式碼剖析工作階段開始之前指定其他一般選項，例如程式碼剖析工具的系統權限以及程式碼剖析資料檔案名稱。|-   [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [如何：序列化符號資訊](../profiling/how-to-serialize-symbol-information.md)<br />-   [如何：設定目前的程式碼剖析工作階段](../Topic/How%20to:%20Set%20the%20Current%20Session.md)<br />-   [如何：設定程式碼剖析權限](../profiling/how-to-set-permissions.md)<br />-   [如何：設定程式碼剖析資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**指定您要收集的資料**：用來設定程式碼剖析工作階段的程序取決於要進行程式碼剖析的目標應用程式類型以及要收集的效能資料類型。|-   [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)<br />-   [使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [使用檢測收集計時詳細資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [如何：分析網頁中的 JavaScript \(ECMA\) 程式碼](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [收集其他效能資料](../profiling/collecting-additional-performance-data.md)|  
|**設定進階組態選項**：對載入多個 Common Language Runtime \(CLR\) 版本的 .NET Framework 應用程式進行程式碼剖析時，您可以指定要剖析的版本。  當效能工作階段中有多個 .exe 檔案時，您可以設定這些二進位檔的啟動順序。|-   [如何：在並存案例中指定要分析的 .NET Framework 執行階段](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)<br />-   [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## 相關章節  
 [控制資料收集](../profiling/controlling-data-collection.md)  
  
## 請參閱  
 [使用程式碼剖析工具](../profiling/performance-explorer.md)