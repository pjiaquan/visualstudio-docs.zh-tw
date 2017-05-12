---
title: "JSON 物件 (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON 物件"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# JSON 物件 (JavaScript)
可提供函式針對 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值和 JavaScript 物件標記法 \(JavaScript Object Notation，JSON\) 表示的格式進行相互轉換的內建物件。  `JSON.stringify` 函式可以將 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值序列化成 JSON 文字，  而 `JSON.parse` 函式則可以將 JSON 文字還原序列化成 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值。  
  
## 語法  
  
```  
  
JSON.[method]  
  
```  
  
## 參數  
 `Method`  
 必要項。  `JSON` 物件的其中一個方法名稱。  
  
## 備註  
 您無法使用 `new` 運算子建立 `JSON` 物件。  如果嘗試這麼做，就會發生錯誤。  不過，您可以覆寫或修改 `JSON` 物件。  
  
 載入指令碼引擎時，引擎會建立 `JSON` 物件，  接著您隨時都能在指令碼中使用該物件的所有方法。  
  
 若要使用內建 `JSON` 物件，請務必不要以指令碼中定義的其他 `JSON` 物件來覆寫內建物件。  您可能需要修改用來偵測 `JSON` 物件是否存在的現有指令碼陳述式，因為這些陳述式會以不同方式進行評估。  這點在下列範例中示範。  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 在上述範例中，`!this.JSON` 在 [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] 中會判斷值為 false，  因此 `if` 陳述式中的程式碼不會執行。  
  
## 函式  
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 請參閱  
 [toJSON 方法 \(日期\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript 物件](../../javascript/reference/javascript-objects.md)   
 [中樞範本範例應用程式 \(Windows 市集\) \(英文\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)