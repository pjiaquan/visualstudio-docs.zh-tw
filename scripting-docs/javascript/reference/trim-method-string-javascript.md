---
title: "trim 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "trim 方法"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim 方法 (字串) (JavaScript)
移除字串前後的空白字元以及行結束字元。  
  
## 語法  
  
```  
  
stringObj.trim()  
```  
  
## 參數  
 `stringObj`  
 必要項。  `String` 物件或字串常值。  `trim` 方法不會修改這個字串。  
  
## 傳回值  
 包含前後空白字元及行結束字元的原始字串已移除。  
  
## 備註  
 移除的字元包括空格、定位字元、換頁字元、歸位字元和換行字元。  如需完整的空白字元和行結束字元清單，請參閱[特殊字元](../../javascript/advanced/special-characters-javascript.md)。  
  
 如需示範如何實作自有 trim 方法的範例，請參閱[原型與原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `trim` 方法。  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [特殊字元](../../javascript/advanced/special-characters-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [捲動、移動瀏覽和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)