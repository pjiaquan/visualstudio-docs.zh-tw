---
title: "資料屬性和存取子屬性 | Microsoft Docs"
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# 資料屬性和存取子屬性
本節包含所有您可能需要之資料屬性與存取子屬性的相關資訊。  
  
### 資料屬性  
 「*資料屬性*」\(Data Property\) 是可以取得並設定其值的屬性。  資料屬性包含其描述項內的 `value` 和 `writable` 屬性。  
  
 下表列出資料屬性 \(Property\) 描述項的屬性 \(Attribute\)。  
  
|資料描述項屬性|描述|預設值|  
|-------------|--------|---------|  
|`value`|屬性的目前值。|`undefined`|  
|`writable`|`true` 或 `false`。  如果 `writable` 設為 `true`，則可以修改屬性值。|`false`|  
|`enumerable`|`true` 或 `false`。  如果 `enumerable` 設為 `true`，則 `for…in` 陳述式可以列舉屬性。|`false`|  
|`configurable`|`true` 或 `false`。  如果 `configurable` 設為 `true`，則表示可以變更屬性 \(Property\) 的屬性 \(Attribute\)，而且可以刪除屬性 \(Property\)。|`false`|  
  
 如果描述項沒有 `value`、`writable`、`get` 或 `set` 屬性 \(Attribute\)，而且指定的屬性 \(Property\) 名稱並不存在，則會加入資料屬性。  
  
 當 `configurable` 屬性為 `false` 且 `writable` 為 `true` 時，可以變更 `value` 和 `writable` 屬性。  
  
#### 不使用 defineProperty 而加入資料屬性  
 如果您加入資料屬性，而不使用 `Object.defineProperty`、`Object.defineProperties` 或 `Object.create` 函式，則 `writable`、`enumerable` 和 `configurable` 屬性都會設定為 `true`。  在加入屬性之後，您就可以使用 `Object.defineProperty` 函式加以修改。  
  
 您可以使用下列方式加入資料屬性：  
  
-   類似 `obj.color = "white";` 中的指派運算子 \(\=\)  
  
-   類似 `obj = { color: "white", height: 5 };` 中的物件常值  
  
-   如[使用常數定義類型](../../javascript/advanced/using-constructors-to-define-types.md)中所述的建構函式  
  
### 存取子屬性  
 每當設定或擷取屬性值時，「*存取子屬性*」\(Accessor Property\) 都會呼叫使用者提供的函式。  存取子屬性 \(Property\) 的描述項包含 `get` 屬性 \(Attribute\) 或 `set` 屬性 \(Attribute\)，或是兩個屬性都包含在內。  
  
 下表列出存取子屬性 \(Property\) 描述項的屬性 \(Attribute\)。  
  
|存取子描述項屬性|描述|預設值|  
|--------------|--------|---------|  
|`get`|傳回屬性值的函式。  此函式沒有任何參數。|`undefined`|  
|`set`|設定屬性值的函式。  它的一個參數包含要指派的值。|`undefined`|  
|`enumerable`|`true` 或 `false`。  如果 `enumerable` 設為 `true`，則 `for…in` 陳述式可以列舉屬性。|`false`|  
|`configurable`|`true` 或 `false`。  如果 `configurable` 設為 `true`，則表示可以變更屬性 \(Property\) 的屬性 \(Attribute\)，而且可以刪除屬性 \(Property\)。|`false`|  
  
 如果未定義 `get` 存取子，而且嘗試存取屬性值，則會傳回 `undefined` 值。  如果未定義 `set` 存取子，而且嘗試為存取子屬性指派值，則不會發生任何事。  
  
### 屬性變更  
 如果物件已經有指定之名稱的屬性，則會修改屬性 \(Property\) 的屬性 \(Attribute\)。  當您修改屬性 \(Property\) 時，未在描述項內指定的屬性 \(Attribute\) 保持不變。  
  
 如果現有屬性 \(Property\) 的 `configurable` 屬性 \(Attribute\) 是 `false`，則唯一允許的修改是將 `writable` 屬性 \(Attribute\) 從 `true` 變更為 `false`。  
  
 您可以將資料屬性變更為存取子屬性，反之亦然。  如果您這麼做，未在描述項內指定的 `configurable` 和 `enumerable` 屬性 \(Attribute\) 會保留在屬性 \(Property\) 中。  未在描述項內指定的其他屬性 \(Attribute\) 會設定為預設值。  
  
 您可以使用 `Object.defineProperty` 函式的多個呼叫，以累加方式定義可設定的存取子屬性。  例如，一個 `Object.defineProperty` 呼叫可能只定義 `get` 存取子。  之後在相同的屬性名稱上呼叫可能會定義 `set` 存取子。  然後此屬性將會同時擁有 `get` 存取子和 `set` 存取子。  
  
 若要取得套用至現有屬性的描述項物件，您可以使用 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
 您可以使用 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md) 和 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md) 來防止修改屬性 \(Property\) 的屬性 \(Attribute\)。