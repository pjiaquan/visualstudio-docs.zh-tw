---
title: "處理序屬性對話方塊、空間索引標籤 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "適用於 Windows NT 的處理序屬性"
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 處理序屬性對話方塊、空間索引標籤
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 \[**空間**\] 索引標籤可以檢查處理序的位址空間。  若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至[處理序檢視](../debugger/processes-view.md)視窗。  選取樹狀結構中的任何處理序節點，然後從 \[**檢視**\] 功能表選取 \[**屬性**\]。  
  
 \[**空間**\] 索引標籤中的可用設定如下：  
  
|Entry|描述|  
|-----------|--------|  
|**顯示標記空間**|使用這個清單方塊可以選取空間的分類 \(影像、對應、保留或未指派\)。|  
|**Executable 位元組**|對選取的分類而言，是這個處理序正在使用的所有位址空間的總和。  Executable memory 是可以被程式執行的記憶體，但是不能被讀寫。|  
|**Exec\-Read\-Only 位元組**|對選取的分類而言，是這個處理序正在使用的所有位址空間 \(與唯讀屬性搭配使用\) 的總和。  Exec\-read\-only 記憶體是可以執行也可以讀取的記憶體。|  
|**Exec\-Read\-Write 位元組**|對選取的分類而言，是這個處理序正在使用的所有位址空間 \(與讀寫屬性搭配使用\) 的總和。  Exec\-read\-write 記憶體是可以被程式執行也可以被讀取和修改的記憶體。|  
|**Exec\-Write Copy 位元組**|對選取的分類而言，是可以被程式執行，也可以被讀取和寫入的所有位址空間的總和。  當處理序之間需要共用記憶體時，就會採取這種保護。  如果共用處理序只會讀取記憶體，則處理序將會全部使用相同的記憶體。  如果共用處理序需要寫入權限，將會產生記憶體複本供處理序使用。|  
|**No\-Access 位元組**|對選取的分類而言，是不允許處理序使用的所有位址空間的總和。  如果嘗寫入或讀取，就會產生存取違規。|  
|**Read\-Only 位元組**|對選取的分類而言，是可以執行也可以讀取的所有位址空間的總和。|  
|**Read\-Write 位元組**|對選取的分類而言，是允許讀取和寫入的所有位址空間的總和。|  
|**Write\-Copy 位元組**|對選取的分類而言，是允許記憶體分享用於讀取，但不能用於寫入的所有位址空間的總和。  當處理序讀取這個記憶體時，可以共用相同的記憶體。  但是，當共用處理序要這個共同記憶體的讀\/寫權限時，會產生該記憶體的複本以供寫入。|