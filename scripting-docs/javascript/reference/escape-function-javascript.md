---
title: "escape 函式 (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "編碼字串物件"
  - "Escape 方法"
  - "十六進位"
  - "字串物件，編碼"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape 函式 (JavaScript)
會將字串編碼，好讓所有電腦都可以讀取。  已取代。  
  
## 語法  
  
```  
escape(charString)   
```  
  
## 備註  
 必要的 `charString` 引數是要編碼的任何 `String` 物件或常值。  
  
 **escape** 函式會傳回一個字串值 \(以 Unicode 格式\)，其中包含 `charstring` 的內容。  而所有的空格、標點符號、腔調字元以及其他非 ASCII 字元均以 `%`*xx* 編碼取代，其中的 *xx* 等於表示該字元的十六進位數字。  例如，空格會當做 "%20" 傳回。  
  
 值大於 255 的字元則以 **%u** *xxxx* 格式儲存。  
  
> [!NOTE]
>  請不要使用 **escape** 函式來編碼統一資源識別元 \(URI\)。  請改用 `encodeURI` 和 `encodeURIComponent` 函式。  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函式](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [unescape 函式](../../javascript/reference/unescape-function-javascript.md)