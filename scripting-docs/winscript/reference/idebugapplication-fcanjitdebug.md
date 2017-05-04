---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
判斷 Just\-In\-Time \(JIT\) 偵錯工具是否已註冊。  
  
## 語法  
  
```  
BOOL FCanJitDebug();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 如果方法成功，以及一個 JIT 偵錯工具已註冊，則方法會傳回 `TRUE`。  否則，會傳回 `FALSE`。  
  
## 備註  
 這個方法會判斷某個 JIT 偵錯工具是否已註冊。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)