---
title: "with 陳述式 (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With 陳述式"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with 陳述式 (JavaScript)
為一個陳述式建立預設物件。  
  
## 語法  
  
```  
with (object) {  
    statements  
}   
```  
  
## 參數  
 `object`  
 預設物件。  
  
 `statements`  
 一個或多個陳述式，`object` 為該陳述式的預設物件。  
  
## 備註  
 `with` 陳述式通常用來減少您在某些情況下必須撰寫的程式碼數量。  
  
> [!WARNING]
>  在 strict 模式中不允許使用 `with`。  使用 `with` 可能會讓程式碼更難閱讀及偵錯，通常應該避免。  
  
## 範例  
 在這個範例中，會重複使用 `Math` 物件：  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## 範例  
 如果您將範例重新撰寫為使用 `with` 陳述式，您的程式碼會變得更簡潔：  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [this 陳述式](../../javascript/reference/this-statement-javascript.md)