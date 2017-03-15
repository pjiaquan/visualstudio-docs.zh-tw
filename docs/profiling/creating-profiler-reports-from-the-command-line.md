---
title: "從命令列建立程式碼剖析工具報告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 從命令列建立程式碼剖析工具報告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfReport** 命令列工具可讓您從程式碼剖析資料 \(.vsp\) 檔案中建立 .xml 或逗點分隔值 \(.csv\) 報告。  VSPerfReport 報告類型非常接近 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的介面的資料表式檢視。  您可以篩選報告只顯示您的程式碼並顯示程式碼剖析資料檔案的一個片段。  如需詳細資訊，請參閱[VSPerfReport](../profiling/vsperfreport.md)。  
  
 您可以透過在 .vsp 檔案中內嵌符號的方式，或是透過建立更小、更快開啟的預先分析報告 \(.vsps\) 檔案，讓程式碼剖析資料檔案變得更容易分享。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**建立基本報告。**建立 VSPerfReport 報告類型的全部或子集。|-   [建立基本報告](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**比較兩個程式碼剖析資料檔案。**建立 "diff" 報告，比較兩個程式碼剖析資料檔案的效能資料。|-   [如何：從命令提示字元建立程式碼剖析工具比較報表](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**檢視呼叫追蹤及 Windows 事件追蹤 \(ETW\) 資料。**建立呼叫追蹤報告，列出您的應用程式函式的每一個進入點及結束點的時間資訊，以及您的函式所其他函式的每一個呼叫。  或是建立一個詳細的清單，列出程式碼剖析期間收集的所有 ETW 事件。|-   [如何：建立呼叫追蹤報表](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**篩選報告。**限制只報告您的程式碼中的函式，或只報告程式碼剖析資料檔案的特定時間。|-   [如何：從命令列篩選報告](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**建立可攜式程式碼剖析資料檔案。**為了更方便共用程式碼剖析的資料，您可以將執行程式碼剖析的符號嵌入 .vsp 檔中。  您也可以建立預先分析的程式碼剖析資料 \(.vsps\) 檔安，這個檔案比較小，開啟速度也比較快。|-   [建立可移植的程式碼剖析資料檔案](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|