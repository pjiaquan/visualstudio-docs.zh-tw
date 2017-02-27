---
title: "如何：從命令列篩選報告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何：從命令列篩選報告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

透過使用 **VSPerfReport**  命令的選項，您可以將報告篩選為程式碼剖析資料檔案的特定時間區段，或是將資料限制在一個或多個處理序或執行緒。  如需此命令的詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
|選項|描述|  
|--------|--------|  
|**StartTime:**\[*Value*\]|只顯示值 \(以毫秒為單位\) 之後收集的資料。|  
|**EndTime:**\[*Value*\]|只顯示值 \(以毫秒為單位\) 之前收集的資料。|  
|**FilterFile:** `VSPFFile`|指定產生自 \[**Visual Studio 效能報告**\] 視窗之篩選檔的位置。|  
|**MsFilter:**\[*StartTime,Duration*\]|只顯示自 `StartTime` 起到 `Duration` 時間長度 \(以毫秒為單位\) 為止的資料。|  
|**Process:**\[*Pid*\]|只顯示來自指定之處理序的資料。|  
|**Thread:**\[*ThreadID*\]|只顯示來自指定之執行緒的資料。|  
|**Thread:**\[*ThreadID,ProcessID*\]|只顯示與指定的處理序相關聯之指定執行緒的資料。|