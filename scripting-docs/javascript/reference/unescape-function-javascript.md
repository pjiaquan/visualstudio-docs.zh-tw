---
title: "unescape 函式 (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape 方法"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape 函式 (JavaScript)
將使用 `escape` 函式編碼的 `String` 物件進行解碼。  已取代。  
  
## 語法  
  
```  
unescape(charString)   
```  
  
## 備註  
 必要的 `charString` 引數是要解碼的 `String` 物件或常值。  
  
 `unescape` 函式會傳回包含 `charstring` 內容的字串值。  所有以 %*xx* 十六進位格式編碼的字元都會以其在 ASCII 字元集的相等字元取代。  
  
 以 **%u** *xxxx* 格式 \(Unicode 字元\) 編碼的字元則都會被以十六進位編碼 *xxxx* 的 Unicode 字元取代。  
  
> [!NOTE]
>  請不要使用 `unescape` 函式來編碼「統一資源識別項」\(Uniform Resource Identifier，URI\)，  而是改用 `decodeURI` 和 `decodeURIComponent` 函式。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 函式](../../javascript/reference/escape-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)