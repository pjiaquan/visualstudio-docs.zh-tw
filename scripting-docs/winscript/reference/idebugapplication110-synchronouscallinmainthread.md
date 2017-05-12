---
title: "IDebugApplication110::SynchronousCallInMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::SynchronousCallInMainThread"
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplication110::SynchronousCallInMainThread
在主執行緒上進行同步呼叫。  
  
> [!IMPORTANT]
>  [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### 參數  
 `pptc`  
 對呼叫的 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md) 物件。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam1`  
 呼叫的第一個參數。  
  
 `dwParam2`  
 呼叫的第二個參數。  
  
 `dwParam3`  
 呼叫的第三個參數。  
  
## 請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)