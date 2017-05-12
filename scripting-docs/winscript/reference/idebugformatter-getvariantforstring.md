---
title: "IDebugFormatter::GetVariantForString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetVariantForString"
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetVariantForString
傳回包含指定字串的變化。  
  
## 語法  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### 參數  
 `pwstrValue`  
 \[out\] 用來儲存字串變數。  
  
 `pvar`  
 \[in\] 包含不同的 `pwstrValue`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回包含指定字串的變化。  
  
## 請參閱  
 [IDebugFormatter 介面](../../winscript/reference/idebugformatter-interface.md)