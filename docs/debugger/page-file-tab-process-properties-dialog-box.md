---
title: "處理序屬性對話方塊、分頁檔索引標籤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "適用於 Windows NT 的處理序屬性"
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# 處理序屬性對話方塊、分頁檔索引標籤
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 \[**分頁檔**\] 索引標籤可以檢查處理序的分頁檔。  若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至[處理序檢視](../debugger/processes-view.md)視窗。  選取樹狀結構中的任何處理序節點，然後從 \[**檢視**\] 功能表選取 \[**屬性**\]。  
  
 \[**分頁檔**\] 索引標籤中的可用設定如下：  
  
|Entry|描述|  
|-----------|--------|  
|**分頁檔位元組**|這個處理序正在分頁檔中使用的目前分頁數目。  分頁檔會儲存處理序所使用但未包含在其他檔案中的資料分頁。  分頁檔是由所有處理序所使用，當其他處理序正在執行時，若分頁檔中空間不足，就會造成錯誤。|  
|**尖峰分頁檔位元組**|這個處理序已在分頁檔中使用的分頁數目上限。|  
|**分頁錯誤**|因這個處理序中執行的執行緒所造成的分頁錯誤數目。  當執行緒參照的虛擬記憶體分頁不是在主記憶體中的工作集時，就會發生分頁錯誤。  因此，如果執行緒在待命清單中且因此已在主記憶體中，或是如果執行緒已經被其他使用共用分頁的處理序使用，就不會從磁碟擷取分頁。|