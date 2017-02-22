---
title: "WriteAllTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

寫入所有執行緒和內容的追蹤記錄。  
  
## 語法  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)