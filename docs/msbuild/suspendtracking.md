---
title: "SuspendTracking | Microsoft Docs"
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
  - "SuspendTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SuspendTracking"
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SuspendTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

暫止目前內容中的追蹤。  
  
## 語法  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## 傳回值  
 如果暫止追蹤，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 與 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集。  
  
## 需求  
 **標頭:** FileTracker.h  
  
## 請參閱  
 [ResumeTracking](../msbuild/resumetracking.md)