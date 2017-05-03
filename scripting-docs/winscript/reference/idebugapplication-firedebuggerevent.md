---
title: "IDebugApplication::FireDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FireDebuggerEvent"
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FireDebuggerEvent
引發泛型事件至偵錯工具的 `IApplicationDebugger` 介面。  
  
## 語法  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### 參數  
 `riid`  
 \[in\] 物件的 GUID。  
  
 `punk`  
 \[in\] 要傳遞的事件物件至偵錯工具。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|方法目前並未執行。|  
  
## 備註  
 完全在應用程式和偵錯工具所定義的 GUID 的語意 \(Semantics\) 和 `IUnknown` 。  
  
 這個方法允許偵錯工具模型的自訂副檔名，它目前尚未實作。  
  
 這個方法會 `IApplicationDebugger::onDebuggerEvent` 呼叫。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)