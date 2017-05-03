---
title: "IDebugProperty::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.SetValueAsString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::SetValueAsString"
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::SetValueAsString
設定屬性的值是從指定的字串。  
  
## 語法  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINT nRadix,  
);  
```  
  
#### 參數  
 `pszValue`  
 \[in\] 要設定的值。  
  
 `nRadix`  
 \[in\] 用來解譯任何數字資訊的基數。  
  
## 傳回值  
 傳回有效的 `HRESULT`，通常 `S_OK`。  
  
## 請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)