---
title: "ArrayBuffer.isView 函式 (ArrayBuffer) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView 函式 (ArrayBuffer)
決定物件是否提供緩衝區的檢視。  
  
## 語法  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### 參數  
 `object`  
 必要項。  要測試的物件。  
  
## 傳回值  
 如果下列任一值為 true 則為 `true`：  
  
-   `object` 是 `DataView` 物件。  
  
-   `object` 是類型陣列。  
  
 否則，方法會傳回 `false`。  
  
## 備註  
  
## 範例  
 下列範例說明如何使用 `isView` 函式測試類型陣列和 `DataView` 物件。  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 請參閱  
 [Uint8ClampedArray 物件](../../javascript/reference/uint8clampedarray-object-javascript.md)