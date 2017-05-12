---
title: "fill 方法 (陣列) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# fill 方法 (陣列) (JavaScript)
以指定的值填入陣列。  
  
## 語法  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### 參數  
 `arrayObj`  
 必要項。  陣列物件。  
  
 `value`  
 必要項。  用來填入陣列的值。  
  
 `start`  
 選擇項。  用來填入陣列值的起始索引。  預設值為 0。  
  
 `end`  
 選擇項。  用來填入陣列值的結束索引。  預設值是 `this` 物件的長度屬性。  
  
## 備註  
 如果 `start` 是負數，`start` 就視為 `length`\+`start`，其中 `length` 是陣列的長度。  如果 `end` 是負數，`end` 就視為 `length`\+`end`。  
  
## 範例  
 下列程式碼範例填入有值的陣列。  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]