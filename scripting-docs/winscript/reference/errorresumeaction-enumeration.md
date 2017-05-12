---
title: "ERRORRESUMEACTION 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION 列舉"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION 列舉
描述如何從執行階段錯誤繼續。  
  
## 語法  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Members  
  
|成員|描述|  
|--------|--------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|重新實作產生錯誤的陳述式。|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|讓語言引擎處理錯誤。|  
|ERRORRESUMEACTION\_SkipErrorStatement|復原之後造成錯誤的陳述式的程式碼。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)