---
title: "SetThreadCount | Microsoft Docs"
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
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設定全域執行緒計數，並將該計數指派給目前執行緒。  
  
## 語法  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### 參數  
 \[in\] `threadCount`  
 要使用的執行緒數目。  
  
## 傳回值  
 如果更新執行緒計數，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 與位元。  
  
## 需求  
 **標頭:** FileTracker.h