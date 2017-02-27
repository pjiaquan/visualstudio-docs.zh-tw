---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

寫入目前內容的記錄檔。  
  
## 語法  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### 參數  
 \[in\] `intermediateDirectory`  
 用來儲存追蹤記錄檔的目錄。  
  
 \[in\] `tlogRootName`  
 記錄檔名稱的根名稱。  
  
## 傳回值  
 如果建立追蹤內容，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 與 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集。  
  
## 需求  
 **標頭:** FileTracker.h  
  
## 請參閱  
 [WriteAllTLogs](../msbuild/writealltlogs.md)