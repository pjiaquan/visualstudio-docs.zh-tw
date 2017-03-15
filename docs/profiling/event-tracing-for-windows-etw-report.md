---
title: "Windows 事件追蹤 (ETW) 報告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW 分析報告"
  - "Windows 事件追蹤分析報告"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Windows 事件追蹤 (ETW) 報告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows 事件追蹤 \(ETW\) 報告會列出記錄在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具效能工作階段中的 ETW 事件。  ETW 資料是收集在二進位 \(.etl\) 檔案中。  
  
> [!NOTE]
>  您無法在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面中顯示 ETW 報告。  
  
-   如需如何從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面使用程式碼剖析工具收集 ETW 的詳細資訊，請參閱 [如何：收集 Windows 事件追蹤 \(ETW\) 資料](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)。  
  
-   如需如何使用 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具收集 ETW 資料的詳細資訊，請參閱[事件](../profiling/events-vsperfcmd.md)。  
  
-   您要使用 **VSReport \/Summary:ETW** 命令來產生 ETW 報告。  如需詳細資訊，請參閱[VSPerfReport](../profiling/vsperfreport.md)。  
  
|資料行|說明|  
|---------|--------|  
|**Timestamp**|識別事件發生的時間。|  
|**處理序 ID**|識別產生事件的處理序。|  
|**執行緒 ID**|識別產生事件的執行緒。|  
|**說明**|識別事件提供者。|  
|**類型**|識別事件類型。|  
|**屬性**|事件的屬性。  每個事件都是逗號分隔的名稱\-值組，並且會以括號括住。|