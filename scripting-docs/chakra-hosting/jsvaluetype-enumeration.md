---
title: "JsValueType 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType 列舉"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType 列舉
JsValueRef 的 JavaScript 類型。  
  
## 語法  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## 成員  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`JsUndefined`|該值是 `undefined` 值。|  
|`JsNull`|該值是 `null` 值。|  
|`JsNumber`|此值為 JavaScript 數字值。|  
|`JsString`|此值為 JavaScript 字串值。|  
|`JsBoolean`|此值為 JavaScript 布林值。|  
|`JsObject`|此值為 JavaScript 物件值。|  
|`JsFunction`|此值為 JavaScript 函式物件值。|  
|`JsError`|此值為 JavaScript 錯誤物件值。|  
|`JsArray`|此值為 JavaScript 陣列物件值。|  
|`JsSymbol`|此值為 JavaScript 符號值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsArrayBuffer`|此值為 JavaScript `ArrayBuffer` 物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsTypedArray`|此值為 JavaScript 類型的陣列物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
|`JsDataView`|此值為 JavaScript `DataView` 物件值。<br /><br /> 只有邊緣模式會支援這個列舉值。|  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)