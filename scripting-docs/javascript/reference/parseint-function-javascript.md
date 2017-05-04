---
title: "parseInt 函式 (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt 方法"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt 函式 (JavaScript)
將字串轉換成整數。  
  
## 語法  
  
```  
parseInt(numString, [radix])   
```  
  
## 參數  
 `numString`  
 必要項。  要轉換為數字的字串。  
  
 `radix`  
 選擇項。  介於 2 到 36 之間的值，用來指定 `numString` 中的數字基底。  如果未提供此引數，則具有 '0x' 前置字元的字串會被視為十六進位。  其他所有字串則會被視為十進位數字。  
  
## 備註  
 `parseInt` 函式傳回的整數值等於 `numString` 中包含的數字。  如果沒有任何 `numString` 前置詞可成功剖析為整數，則會傳回 `NaN` \(非數字\)。  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 您可以使用 `isNaN` 函式來測試 `NaN`。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  從 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] 開始，`parseInt` 函式不會將具有前置 '0' 的字串視為八進位。  但是當您不使用 `parseInt` 函式時，具有前置 '0' 的字串仍然可以被解譯為八進位。  如需八進位整數的詳細資訊，請參閱[資料類型](../../javascript/data-types-javascript.md)。  
  
## 請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 函式](../../javascript/reference/parsefloat-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)   
 [valueOf 方法 \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)