---
title: "decodeURIComponent 函式 (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent 方法"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent 函式 (JavaScript)
取得已編碼之統一資源識別元 \(Uniform Resource Identifier，URI\) 元件的未編碼版本。  
  
## 語法  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## 備註  
 必要的 `encodedURIString` 引數的值表示已編碼的 URI 元件。  
  
 URIComponent 是完整 URI 的一部分。  
  
 如果 `encodedURIString` 無效，就會發生 URIError。  
  
## 範例  
 下列程式碼會先編碼 URI 字串，然後加以解碼。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)