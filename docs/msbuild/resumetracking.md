---
title: "ResumeTracking | Microsoft Docs"
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
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

繼續目前內容中的追蹤。  
  
## 語法  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## 傳回值  
 如果恢復追蹤，會設定 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) 與 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集。  如果因內容無法使用而無法繼續追蹤，則會傳回 [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True)。  
  
## 需求  
 **標頭:** FileTracker.h  
  
## 請參閱  
 [SuspendTracking](../msbuild/suspendtracking.md)