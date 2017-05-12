---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
為呼叫端提供一種機制。在偵錯工具執行緒上執行程式碼。  
  
## 語法  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### 參數  
 `pptc`  
 \[out\] 呼叫的物件。  
  
 `dwParam1`  
 \[in\] 傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第一個參數。  
  
 `dwParam2`  
 \[in\] 傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第二個參數。  
  
 `dwParam3`  
 \[in\] 傳遞至 `IDebugThreadCall::ThreadCallHandler` 方法的第三個參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 語言引擎和主應用程式通常會使用這個方法會實作無限制執行緒物件在其單一執行緒的實作頂端。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall 介面](../../winscript/reference/idebugthreadcall-interface.md)