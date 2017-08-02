---
title: "建立 JavaScript IntelliSense 的 JSDoc 註解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 建立 JavaScript IntelliSense 的 JSDoc 註解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 中的 IntelliSense 會顯示您使用標準 JSDoc 註解加入指令碼的資訊。  您可以使用 JSDoc 註解來提供程式碼項目 \(例如函式、欄位和變數\) 的相關資訊。  
  
## JSDoc 註解標記  
 下列標準 JSDoc 註解標記是由 IntelliSense 用於顯示您程式碼的相關資訊。  
  
|JSDoc 標記|語法|備註|  
|--------------|--------|--------|  
|@deprecated|@deprecated *描述*|指定取代函式或方法。|  
|@description|@description *描述*|指定函式或方法的描述。|  
|@param|@param {*類型*} *參數名稱**描述*|指定函式或方法中之參數的資訊。<br /><br /> TypeScript 也支援 @paramTag。|  
|@property|@property {*類型*} *屬性名稱*|指定欄位或物件上所定義成員的資訊，包括描述。|  
|@returns|@returns {*類型*}|指定傳回值。<br /><br /> 對於 TypeScript，請使用 @returnType，而不要使用 @returns。|  
|@summary|@summary *描述*|指定函式或方法的描述 \(與 @description 相同\)。|  
|@type|@type {*類型*}|指定常數或變數的類型。|  
|@typedef|@typedef {*類型*} *自訂類型名稱*|指定自訂類型。|  
  
### 範例  
 下列範例將示範如何針對名為 `getArea` 的函式使用 @description、@param，和 @return JSDoc 標記。  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 在上述範例中，當您輸入 `getArea` 的左括號時，IntelliSense 會顯示描述、參數和傳回的資訊。  
  
 ![函式的 IntelliSense 資訊](~/docs/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 下列範例將示範如何使用 @typedef 標記搭配 @property 標記。  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 下列範例將示範 @type JSDoc 標記的用法。  如本範例所示，在初始星號配對 \(\*\*\) 之後不需要單一星號 \(\*\)。  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 下列範例將示範如何使用 @deprecated JSDoc 標記。  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```