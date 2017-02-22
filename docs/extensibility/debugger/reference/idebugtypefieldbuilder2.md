---
title: "IDebugTypeFieldBuilder2 | Microsoft Docs"
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
  - "IDebugTypeFieldBuilder2 介面"
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

延伸 **IDebugTypeFieldBuilder** ，才能建立陣列型別。  
  
## 語法  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## 呼叫者的備忘稿  
 這個介面可以取自符號提供者。  
  
## 方法  
 除了在方法[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|建立指定型別和大小的陣列。|  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll