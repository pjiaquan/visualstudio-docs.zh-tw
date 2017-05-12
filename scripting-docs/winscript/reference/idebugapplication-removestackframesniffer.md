---
title: "IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveStackFrameSniffer"
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveStackFrameSniffer
從應用程式移除堆疊框架列舉值提供者。  
  
## 語法  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### 參數  
 `dwCookie`  
 \[in\] Cookie 是 `AddStackFrameSniffer` 方法傳回，則當堆疊框架列舉值提供者加入。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法 `RemoveStackFrameSniffer` 從應用程式移除堆疊框架列舉值提供者。  
  
## 請參閱  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer 介面](../../winscript/reference/idebugstackframesniffer-interface.md)