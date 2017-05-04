---
title: "IJsEnumDebugProperty::Next 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsEnumDebugProperty::Next 方法
讀取這個物件的屬性。  
  
## 語法  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### 參數  
 `count`  
 \[in\] 要讀取的屬性數目。  
  
 `ppDebugProperty`  
 \[out\] 代表屬性瀏覽器的物件。  
  
 `pActualCount`  
 \[out\] 物件屬性的實際數目。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsEnumDebugProperty 介面](../../winscript/reference/ijsenumdebugproperty-interface.md)