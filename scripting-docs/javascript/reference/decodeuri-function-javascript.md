---
title: "decodeURI 函式 (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI 方法"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI 函式 (JavaScript)
取得已編碼之統一資源識別元 \(URI\) 的解碼版本。  
  
## 語法  
  
```  
decodeURI(URIstring)  
```  
  
## 備註  
 必要的 `URIstring` 引數是表示編碼 URI 的值。  
  
 請使用 `decodeURI` 函式，不要使用已被取代的 `unescape` 函式。  
  
 `decodeURI` 函式會傳回字串值。  
  
 如果 `URIString` 無效，就會發生 URIError。  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 範例  
 下列程式碼會先編碼 URI 元件，然後加以解碼。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global 物件](../../javascript/reference/global-object-javascript.md)