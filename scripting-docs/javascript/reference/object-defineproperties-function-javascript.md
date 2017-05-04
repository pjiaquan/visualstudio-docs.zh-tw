---
title: "Object.defineProperties 函式 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Object.defineProperties 函式 [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties 函式 (JavaScript)
將一個或多個屬性 \(Property\) 加入至物件，並且 \(或者\) 修改現有屬性 \(Property\) 的屬性 \(Attribute\)。  
  
## 語法  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## 參數  
 `object`  
 必要項。  要新增或修改屬性的目標物件。  這可以是原生 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件或 DOM 物件。  
  
 `descriptors`  
 必要項。  包含一個或多個描述元物件的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  每個描述元物件都會描述資料屬性 \(Property\) 或存取子屬性 \(Property\)。  
  
## 傳回值  
 已傳遞給函式的物件。  
  
## 備註  
 `descriptors` 引數是包含一個或多個描述元物件的物件。  
  
 「*資料屬性*」\(Data Property\) 是可儲存和擷取值的屬性。  資料屬性 \(Property\) 描述元包含 `value` 屬性 \(Attribute\)、`writable` 屬性 \(Attribute\)，或兩者都包含。  如需詳細資訊，請參閱[資料屬性和存取子屬性](../../javascript/advanced/data-properties-and-accessor-properties.md)。  
  
 每當設定或擷取屬性值時，「*存取子屬性*」\(Accessor Property\) 都會呼叫使用者提供的函式。  存取子屬性 \(Property\) 描述元包含 `set` 屬性 \(Attribute\) 或 `get` 屬性 \(Attribute\)，或兩者都包含。  
  
 如果物件已包含具有指定之名稱的屬性 \(Property\)，則該屬性 \(Property\) 的屬性 \(Attribute\) 會遭修改。  如需詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
 若要建立新物件並為其加入新屬性，可以使用 [Object.create 函式](../../javascript/reference/object-create-function-javascript.md)。  
  
## 加入屬性  
 在下列範例中，`Object.defineProperties` 函式會將資料屬性與存取子屬性加入至使用者定義的物件。  
  
 此範例會使用物件常值建立包含 `newDataProperty` 和 `newAccessorProperty` 描述元物件的 `descriptors` 物件。  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 如同前面範例一般，下列範例會以動態方式 \(而不使用物件常值\) 加入屬性。  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## 修改屬性  
 若要修改物件屬性 \(Property\) 的屬性 \(Attribute\)，請加入下列程式碼。  `Object.defineProperties` 函式會修改 `newDataProperty` 的 `writable` 屬性，以及修改 `newAccessorProperty` 的 `enumerable` 屬性。  因為物件並沒有名稱為 `anotherDataProperty` 的屬性，所以函式將這個屬性加入至物件。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## 需求  
 Internet Explorer 9 標準、Internet Explorer 10 標準和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式都支援。  Internet Explorer 8 只支援 DOM 物件，不支援其他物件。  
  
## 請參閱  
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 函式](../../javascript/reference/object-create-function-javascript.md)   
 [Object 物件](../../javascript/reference/object-object-javascript.md)