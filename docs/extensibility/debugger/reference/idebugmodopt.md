---
title: "IDebugModOpt | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugModOpt 介面"
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModOpt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示偵錯的選擇性修飾詞。  
  
## 語法  
  
```  
IDebugModOpt : IUnknown  
```  
  
## 呼叫者的備忘稿  
 取自[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示類別或方法。  
  
## 方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|擷取一份選擇性修飾詞。|  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll