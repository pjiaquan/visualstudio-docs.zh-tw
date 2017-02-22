---
title: "StopTrackingAndCleanup | Microsoft Docs"
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
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

停止所有追蹤並釋放追蹤工作階段使用的任何記憶體。  
  
## 語法  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## 傳回值  
 如果停止追蹤，傳回含有 [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) 位元集的 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)。  
  
## 需求  
 **標頭:** FileTracker.h  
  
## 請參閱  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)