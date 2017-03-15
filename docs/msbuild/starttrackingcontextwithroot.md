---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用指定根標記的回應檔案啟動追蹤內容。  
  
## 語法  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### 參數  
 \[in\] `intermediateDirectory`  
 用來儲存追蹤記錄檔的目錄。  
  
 \[in\] `taskName`  
 識別追蹤內容。  這個名稱用來建立記錄檔名稱。  
  
 \[in\] `rootMarkerResponseFile`  
 回應檔 \(包含根標記\) 的路徑名稱。  根名稱用於群組內容的所有追蹤。  
  
## 傳回值  
 如果建立追蹤內容，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 與 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集。  
  
## 需求  
 **標頭:** FileTracker.h  
  
## 請參閱  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)