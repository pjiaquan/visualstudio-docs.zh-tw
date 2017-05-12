---
title: "encodeURIComponent 函式 (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent 方法"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent 函式 (JavaScript)
將文字字串編碼成有效的統一資源識別元 \(URI\) 元件。  
  
## 語法  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## 備註  
 必要的 `encodedURIString` 引數的值表示已編碼的 URI 元件。  
  
 `encodeURIComponent` 函式會傳回已編碼的 URI。  如果將結果傳給 `decodeURIComponent`，就會傳回原始字串。  因為 `encodeURIComponent` 函式會將所有字元編碼，所以請特別注意字串是否表示路徑，像是 \/folder1\/folder2\/default.html。  系統會將斜線字元編碼，而且如果此編碼當做要求傳至 Web 伺服器就會無效。  如果字串包含一個以上的單一 URI 元件，請使用 `encodeURI` 函式。  
  
## 範例  
 下列程式碼會先編碼 URI 元件，然後加以解碼。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)