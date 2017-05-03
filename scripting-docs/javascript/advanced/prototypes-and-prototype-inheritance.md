---
title: "原型與原型繼承 | Microsoft Docs"
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
  - "原型 [JavaScript]"
  - "原型繼承 [JavaScript]"
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 原型與原型繼承
在 JavaScript 中，`prototype` 是函式的屬性，也是由建構函式所建立之物件的屬性。  函式的原型就是物件。  當函式本身就是建構函式時，原型就會派上用場。  
  
```javascript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 在上述範例中，`Vehicle` 函式的原型即為 `Vehicle` 建構函式所具現化之任何物件的原型。  
  
## 使用原型添加屬性和方法  
 您可以使用 `prototype` 屬性，為物件添加屬性和方法，即使是已經建立的物件也適用：  
  
```javascript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 `testColor` 的值是 "red"。  
  
 您甚至可以為預先定義的物件添加屬性和方法。  例如，您可以為 `String` 原型物件定義 `Trim` 方法，而指令碼中的所有字串都會繼承這個方法。  
  
```javascript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### 使用原型並搭配 Object.create，從某個物件衍生另一個物件  
 `prototype` 物件可以用來從某個物件衍生另一個物件。  例如，您可以使用 [Object.create](../../javascript/reference/object-create-function-javascript.md) 函式，並利用先前所定義 `Vehicle` 物件的原型來衍生新的物件 `Bicycle` \(並且添加所需的新屬性\)。  
  
```javascript  
var Bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 `Bicycle` 物件具有 `wheels`、`engine`、`color` 和 `pedals` 屬性，而且其原型為 `Vehicle.prototype`。  JavaScript 引擎會在 `Bicycle` 上找到 `pedals` 屬性，然後再透過查詢原型鏈結，找到 `Vehicle` 上的 `wheels`、`engine` 和 `color` 屬性。  
  
### 變更物件的原型  
 在 Internet Explorer 11 中，您可以使用 [\_\_proto\_\_](../../javascript/reference/proto-property-object-javascript.md) 屬性以新的原型來取代物件或函式的內部原型。  當您使用這個屬性時，就會繼承新原型的屬性和方法以及它的原型鏈結中的其他屬性和方法。  
  
 下面範例會示範如何變更物件的原型。  這個範例會示範當您變更物件的原型時，該物件所繼承的屬性是如何變更的。  
  
```javascript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```