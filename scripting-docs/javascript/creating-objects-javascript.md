---
title: "建立物件 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "建構函式"
  - "建構函式, 包括屬性與方法"
  - "建立物件"
  - "建立物件, 關於建立物件"
  - "建立物件, 建構函式"
  - "建立物件, 原型"
  - "自訂物件"
  - "自訂物件, 建立"
  - "建構函式"
  - "初始化物件, 使用建構函式"
  - "物件, 建立 [JavaScript]"
  - "原型物件"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 建立物件 (JavaScript)
您有數種方式可以使用 JavaScript 建立專屬物件。  您可以直接具現化[Object 物件](../javascript/reference/object-object-javascript.md)，然後加入專屬屬性和方法。  或者，您可以使用物件常值標記法來定義物件。  您也可以使用建構函式來定義物件。  如需使用建構函式的詳細資訊，請參閱[使用常數定義類型](../javascript/advanced/using-constructors-to-define-types.md)。  
  
## 範例  
 下列程式碼示範如何具現化物件，以及加入一些屬性。  在此情況下，只有 `pasta` 物件具有 `grain`、`width` 和 `shape` 屬性。  
  
```javascript  
var pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## 物件常值  
 當您只要想為物件建立一個執行個體時，也可以使用物件常值標記法。  下列程式碼示範如何使用物件常值標記法來具現化物件。  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 您也可以在建構函式內使用物件常值。  
  
> [!CAUTION]
>  只有 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 才支援下面所述的功能。  
  
 在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中，您可以使用縮寫語法來建立物件常值。  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 下列範例示範如何使用縮寫語法以在物件常值中定義方法。  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 您也可以在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中於物件常值中動態設定屬性名稱。  下列程式碼範例會使用 set 語法動態建立物件的屬性名稱。  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 下列程式碼範例會使用 get 語法動態建立物件的屬性名稱。  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 下列程式碼範例會使用 [arrow function 語法](../javascript/functions-javascript.md)將 42 附加至屬性名稱來建立計算屬性。  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```