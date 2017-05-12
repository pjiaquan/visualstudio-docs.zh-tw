---
title: "IDebugStackFrame::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDebugProperty"
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDebugProperty
傳回目前框架的屬性瀏覽器。  
  
## 語法  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### 參數  
 `ppDebugProp`  
 \[in\] 目前框架的屬性瀏覽器中。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回目前框架的屬性瀏覽器。  
  
## 請參閱  
 [IDebugStackFrame 介面](../../winscript/reference/idebugstackframe-interface.md)