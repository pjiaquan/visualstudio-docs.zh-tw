---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
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
  - "IDebugWindowsComputerPort2 介面"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

可讓查詢目標電腦的相關資訊。  
  
## 語法  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由連接埠的工作階段的偵錯管理員 」 的物件。  
  
## 方法  
 下表顯示的方法`IDebugWindowsComputerPort2`。  
  
|方法|描述|  
|--------|--------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|擷取電腦的相關資訊，在其上執行的偵錯工具。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll