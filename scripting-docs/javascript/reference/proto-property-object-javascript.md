---
title: "__proto__ 屬性 (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__ 屬性 (Object) (JavaScript)
包含指定之物件內部原型的參考。  
  
## 語法  
  
```  
object.__proto__  
```  
  
#### 參數  
 `object`  
 必要項。  要在其上設定原型的物件。  
  
## 備註  
 `__proto__` 屬性可用來設定物件的原型。  
  
 物件或函式會繼承新原型的所有方法和屬性，以及在新原型的原型鏈結中的所有方法和屬性。  物件只能有一個原型 \(不包括原型鏈結中的繼承原型\)，因此在呼叫 `__proto__` 屬性時，您會取代上一個原型。  
  
 您只能對可延伸物件設定原型。  如需詳細資訊，請參閱 [Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)。  
  
> [!NOTE]
>  `__proto__` 屬性名稱的開頭和結尾是兩個底線。  
  
## 範例  
 下列程式碼範例會示範如何設定物件的原型。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## 範例  
 下列程式碼範例會示範如何藉由將屬性加入至原型，將屬性加入至物件。  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## 範例  
 下列程式碼範例會在 `String` 物件上設定新原型，將屬性加入至這個物件。  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [原型與原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)