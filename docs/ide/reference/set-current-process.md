---
title: "設定目前處理序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess 命令"
  - "設定目前執行緒命令"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# 設定目前處理序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在偵錯工具中，將指定的處理序設定為現用的處理序。  
  
## 語法  
  
```  
Debug.SetCurrentProcess index  
```  
  
## 引數  
 `index`  
 必要項。  這是處理序的索引。  
  
## 備註  
 進行偵錯時，您可以附加至多個處理序，但是無論在任何時間，偵錯工具都只有一個使用中處理序。  您可以使用 `SetCurrentProcess` 命令設定現用的處理序。  
  
## 範例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)