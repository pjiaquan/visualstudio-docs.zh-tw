---
title: "處理序屬性對話方塊、一般索引標籤 | Microsoft Docs"
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
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 處理序屬性對話方塊、一般索引標籤
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 \[**一般**\] 索引標籤可以尋找更多有關特定處理序的資訊。  若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至[處理序檢視](../debugger/processes-view.md)視窗。  選取樹狀結構中的任何處理序節點，然後從 \[**檢視**\] 功能表選取 \[**屬性**\]。  
  
 \[**一般**\] 索引標籤中的可用設定如下：  
  
|Entry|描述|  
|-----------|--------|  
|**模組名稱**|模組名稱。|  
|**處理序 ID**|此處理序的唯一 ID。  處理序 ID 編號會重複使用，因此只在處理序存留期中識別處理序。  當執行程式時會建立 Process 物件型別。  處理序中的所有執行緒會共用相同的位址空間並且可以存取相同的資料。|  
|**優先權基底**|這個處理序的目前基礎優先權。  處理序中的執行緒可以相對於處理序的基礎優先權，提高及降低本身的基礎優先權。|  
|**執行緒**|這個處理序中目前作用中的執行緒數目。|  
|**CPU 時間**|花費在這個處理序及其執行緒的總 CPU 時間。  等於使用者時間加上授權的時間。|  
|**使用者時間**|這個處理序的執行緒以使用者模式在非閒置執行緒中，執行程式碼所花費的累計耗用時間。  應用程式會以使用者模式執行，與視窗管理員及圖形引擎之類的子系統一樣。|  
|**授權的時間**|這個處理序以授權模式在非閒置執行緒中，所執行的總耗用時間。  服務層、Executive 常式以及核心程式都會以授權模式執行。  除了圖形卡和印表機之外，大部分裝置的驅動程式也是以授權模式執行。  某些 Windows 為您的應用程式所做的工作，可能會出現在除了授權時間以外的其他子系統處理序中。|  
|**已耗用時間**|這個處理序已經執行的總耗用時間。|