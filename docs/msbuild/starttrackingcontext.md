---
title: "StartTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

啟動追蹤內容。  
  
## 語法  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### 參數  
 \[in\] `intermediateDirectory`  
 用來儲存追蹤記錄檔的目錄。  
  
 \[in\] `taskName`  
 識別追蹤內容。  這個名稱用來建立記錄檔名稱。  
  
## 傳回值  
 如果建立追蹤內容，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 與 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集。  
  
## 需求  
 **標頭:** FileTracker.h