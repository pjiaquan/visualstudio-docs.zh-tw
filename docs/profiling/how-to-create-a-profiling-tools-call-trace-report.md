---
title: "如何：建立程式碼剖析工具呼叫追蹤報表 | Microsoft Docs"
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
  - "ETW [Visual Studio ALM], 檢視資料"
  - "效能工具, 檢視 ETW 資料"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：建立程式碼剖析工具呼叫追蹤報表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的「*呼叫追蹤報表*」\(Call Trace Report\) 會列出您的應用程式函式的每一個進入點及結束點的時間資訊，以及您的函式對其他函式的每一個呼叫。  呼叫追蹤報告僅適用於使用檢測方法收集的程式碼剖析資料。  
  
> [!NOTE]
>  您無法在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中顯示呼叫追蹤報告。  您必須使用 **VSPerfReport** 命令列工具產生逗號分隔值 \(.csv\) 或 Xml 檔案。  如需這個工具的詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
### 若要建立呼叫追蹤報告  
  
1.  開啟 \[**命令提示字元**\] 視窗。  
  
2.  在命令提示字元中輸入下列命令：  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|程式碼剖析工具命令列工具的路徑。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。|  
    |*VSPFile*|程式碼剖析資料 \(.vsp 或 .vsps\) 檔案。  接受完整與部分路徑。|  
    |Xml|產生 Xml 格式報告。|  
  
## 請參閱  
 [如何：收集 Windows 事件追蹤 \(ETW\) 資料](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [程式碼剖析工具 API](../profiling/profiling-tools-apis.md)