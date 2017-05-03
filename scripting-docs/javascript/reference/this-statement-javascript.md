---
title: "this 陳述式 (JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "建構函式, 參考目前物件"
  - "this 陳述式"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this 陳述式 (JavaScript)
參考目前的物件。  
  
## 語法  
  
```  
this.property  
```  
  
## 備註  
 必要的 `property` 引數是目前物件的其中一個屬性  
  
 `this` 關鍵字可以在物件建構函式中用來參考目前的物件。  
  
## 範例  
 在以下範例中，**this** 會參考剛建立的 Car 物件，並且會指派三個屬性的值：  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 如果在任何其他物件的範圍之外使用 **this** 關鍵字，這個關鍵字通常會參考 **window** 物件。  不過，在事件處理常式內部，`this` 會參考引發事件的 DOM 項目。  
  
 在下列程式碼 \(適用於 Internet Explorer 9 \(含\) 以後版本\) 中，事件處理常式會列印 ID 為 "clicker" 之按鈕的字串版本。  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)