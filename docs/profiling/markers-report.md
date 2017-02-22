---
title: "標記報告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 標記報告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

標記報表會透過時間圖文框的方式顯示標記的清單。平移或縮放或隱藏歸位字元，可能會導致標記出現或消失。  報告包含每個標記的資訊:  
  
-   在啟動後相對於追蹤的開頭的時間。  
  
-   它的持續期間。  因為它們代表暫時性，期間的旗標和訊息都為零。  
  
-   產生它執行緒的 ID。  
  
-   提供者產生的 Windows 事件追蹤 \(ETW\) 。  
  
-   從標記系列所寫的。  
  
-   事件分類所屬的。  
  
-   它的重要性程度。  
  
-   其型別 \(間距、旗標、訊息\)。  
  
-   代表意義的高階說明  
  
 選取 \[**匯出**\] 按鈕儲存標記報告為 CSV 檔案。  您可以在其他應用程式或工具的 CSV 檔中使用資料。  
  
> [!NOTE]
>  標記報表可以顯示 1,000 個標記。  若要查看所有的資料標記，匯出報告全文為 CSV 檔案。