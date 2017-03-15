---
title: "收集 .NET 記憶體配置和存留期資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 記憶體程式碼剖析方法"
  - "程式碼剖析工具，.NET 記憶體方法"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 收集 .NET 記憶體配置和存留期資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具支援 .NET 記憶體配置和物件存留期資料的收集，可協助您偵測應用程式中記憶體相關的效能問題。  
  
-   有關 .NET 記憶體配置的資料包括配置的 .NET Framework 記憶體物件大小和數量。  
  
-   物件存留期資料包括在三代記憶體回收中回收的 .NET Framework 記憶體物件大小和數量。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 您可以使用取樣或檢測程式碼剖析方法收集資料。  
  
-   使用取樣方法時，程式碼剖析工具會追蹤啟動或附加的程序所產生的所有 .NET 記憶體配置和物件。  
  
-   使用檢測方法時，程式碼剖析工具只會追蹤檢測模組所產生的 .NET 記憶體配置和物件。  
  
> [!IMPORTANT]
>  當您利用取樣方法收集 .NET 記憶體資料 \(配置、物件存留期或兩者\) 時，會忽略所有使用者指定的取樣事件，並且使用適當的記憶體配置事件收集資料。  
  
 如果您啟用 .NET 記憶體配置的程式碼剖析，會同時啟用 \[配置檢視\]。  如果您啟用 .NET 存留期資料的程式碼剖析，則會同時啟用 \[物件存留期檢視\]。  如需詳細資訊，請參閱[配置檢視](../profiling/dotnet-memory-allocations-view.md)與[物件存留期檢視](../profiling/object-lifetime-view.md)。  
  
 如需如何使用程式碼剖析工具命令列工具收集 .NET 記憶體資料的詳細資訊，請參閱[從命令列使用程式碼剖析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)中的＜使用 .NET 記憶體方法收集記憶體配置和物件存留期資料＞。  
  
### 若要收集 .NET 記憶體資料  
  
1.  在 \[**效能總管**\] 中，以滑鼠右鍵按一下 \[效能工作階段\]，然後按一下 \[**屬性**\]。  
  
2.  在 \[*Performance Session***屬性頁**\] 對話方塊中，按一下 \[**一般**\] 索引標籤，並選取 \[**收集 .NET 物件配置資訊**\] 核取方塊。  
  
3.  若要收集 .NET 物件存留期資料，請選取 \[**同時收集 .NET 物件存留期的資訊**\] 核取方塊。  
  
## 一般工作  
 您可以在效能工作階段的 *Performance Session* \[**屬性頁**\] 對話方塊中指定其他選項。  若要開啟此對話方塊：  
  
-   在 \[**效能總管**\] 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 \[**屬性**\]。  
  
 下表中的工作說明當您收集 .NET 記憶體資料時，可以在 \[*Performance Session* **屬性頁**\] 對話方塊中指定的選項。  
  
|工作|相關內容|  
|--------|----------|  
|在 \[**一般**\] 頁面上，為產生的程式碼剖析資料 \(.vsp\) 檔案指定命名的詳細資料。|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [如何：設定程式碼剖析資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在 \[**啟動**\] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請選擇要啟動的應用程式。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 \[**階層互動**\] 頁面上，將 ADO.NET 呼叫資料加入至程式碼剖析執行中。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 \[**Windows 事件**\] 頁面上，指定一個或多個要透過取樣資料收集的 Windows 事件追蹤 \(ETW\) 事件。|-   [如何：收集 Windows 事件追蹤 \(ETW\) 資料](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|在 \[**Windows 計數器**\] 頁面上，指定一個或多個要加入至程式碼剖析資料中做為標記的作業系統效能計數器。|-   [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|  
|如果您的應用程式模組使用多個版本，請在 \[**進階**\] 頁面上，指定要進行程式碼剖析的 .NET Framework 執行階段版本。  根據預設，會對第一個載入的版本進行程式碼剖析。|-   [如何：在並存案例中指定要分析的 .NET Framework 執行階段](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|  
  
## 檢測工作  
 下表中的工作為 \[**屬性頁**\] 對話方塊中，使用檢測方法進行程式碼剖析的特定選項。  
  
|工作|相關內容|  
|--------|----------|  
|在 \[**二進位檔**\] 頁面中，指定已檢測之模組複本的位置。  根據預設，原始的二進位檔會移至備份資料夾。|-   [如何：重新配置所檢測的二進位檔](../profiling/how-to-relocate-instrumented-binaries.md)|  
|在 \[**檢測**\] 頁面上，從程式碼剖析中排除小型函式以減少程式碼剖析的額外負荷、對 ASP.NET 網頁中的 JavaScript 程式碼進行程式碼剖析，並在檢測程序前後於命令提示字元指定要執行的命令。|-   [如何：從檢測排除或包含 Short 函式](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)<br />-   [如何：分析網頁中的 JavaScript \(ECMA\) 程式碼](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [如何：指定檢測前置和檢測後續命令](../Topic/How%20to:%20Specify%20Pre-%20and%20Post-Instrument%20Commands.md)|  
|在 \[**CPU 計數器**\] 頁面上，指定一個或多個要加入至程式碼剖析資料中的處理器效能計數器。|-   [如何：收集 CPU 計數器資料](../profiling/how-to-collect-cpu-counter-data.md)|  
|在 \[**進階**\] 頁面上，指定需要的任何 VSInstr.exe 選項，例如要包含或排除特定函式的選項。  如需 VSInstr 選項的詳細資訊，請參閱 [VSInstr](../profiling/vsinstr.md)。|-   [如何：指定其他的檢測選項](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)<br />-   [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)