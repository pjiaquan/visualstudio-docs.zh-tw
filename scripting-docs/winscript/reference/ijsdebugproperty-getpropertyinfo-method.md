---
title: "IJsDebugProperty::GetPropertyInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProperty.GetPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProperty::GetPropertyInfo 方法
取得這個物件的資訊。  
  
## 語法  
  
```  
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### 參數  
 `nRadix`  
 \[in\] 要使用的基數。  
  
 `pPropertyInfo`  
 \[out\] 物件的相關資訊。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugProperty 介面](../../winscript/reference/ijsdebugproperty-interface.md)