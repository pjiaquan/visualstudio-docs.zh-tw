---
title: "JsSetIndexedPropertiesToExternalData 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsSetIndexedPropertiesToExternalData 函式
將物件的索引屬性設定為外部資料。  這個外部資料將會做為物件索引屬性的後備存放區，並以類似具類型陣列的方式來存取。  
  
## 語法  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### 參數  
 `object`  
 要處理的物件。  
  
 `data`  
 要做為物件索引屬性之後備存放區的外部資料。  
  
 `arrayType`  
 外部資料中的陣列項目類型。  
  
 `elementLength`  
 外部資料中的陣列項目數。  
  
## 傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## 備註  
 需要使用中指令碼內容。  
  
 只有邊緣模式才支援這個 API。  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)