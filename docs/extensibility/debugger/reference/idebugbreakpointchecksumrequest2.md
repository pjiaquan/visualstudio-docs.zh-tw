---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBreakpointChecksumRequest2 介面"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示中斷點要求的文件加總檢查碼。  
  
## 語法  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## 實作器注意事項  
 藉由實作[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯套件，並由偵錯引擎。  
  
## 方法  
 下表顯示的方法`IDebugBreakpointChecksumRequest2`。  
  
|方法|描述|  
|--------|--------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|擷取文件的總和檢查碼中斷點要求指定的總和檢查碼演算法的唯一識別項使用。|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|判定是否加總檢查碼已啟用這份文件。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll