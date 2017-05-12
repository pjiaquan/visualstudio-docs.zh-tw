---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
處理自訂應用程式事件。  
  
## 語法  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### 參數  
 `riid`  
 \[in\] 物件的介面識別項。  
  
 `punk`  
 \[in\] 事件物件，實作介面。 `riid`定義。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|方法目前並未執行。|  
  
## 備註  
 完全在應用程式和偵錯工具所定義的 `IUnknown` 的語意。  
  
 這個方法允許偵錯工具模型的自訂副檔名，它目前尚未實作。  
  
 `IDebugApplication::FireDebuggerEvent` ，當呼叫時，呼叫這個方法。  
  
## 請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)