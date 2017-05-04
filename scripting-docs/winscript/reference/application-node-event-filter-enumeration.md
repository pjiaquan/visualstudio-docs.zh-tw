---
title: "APPLICATION_NODE_EVENT_FILTER 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER 的常數"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER 列舉
指定在節點型別排除篩選程式碼檔案。  使用在 [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 和 [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  這些常數都是 PDM v10.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|傳送所有事件。|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|排除匿名程式碼結構。  JScript Runtime 使用這些節點。 `new Function([args,] <code>)'`。|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|排除 eval 的程式碼。  JScript Runtime 使用這些節點為 eval 的支援。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)