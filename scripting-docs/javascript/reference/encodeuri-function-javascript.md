---
title: "encodeURI 函式 (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI 方法"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI 函式 (JavaScript)
將文字字串編碼成有效的「統一資源識別項」\(Uniform Resource Identifier，URI\)。  
  
## 語法  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## 備註  
 必要的 `URIString` 引數是表示編碼 URI 的值。  
  
 `encodeURI` 函式會傳回已編碼的 URI。  如果將結果傳給 `decodeURI`，就會傳回原始字串。  `encodeURI` 函式不會對 ":"、"\/"、";" 和 "?" 字元進行編碼，  因此請使用 `encodeURIComponent` 來對這些字元進行編碼。  
  
## 範例  
 下列程式碼會先編碼 URI 字串，然後加以解碼。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)