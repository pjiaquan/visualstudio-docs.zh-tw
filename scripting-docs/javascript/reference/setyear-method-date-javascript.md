---
title: "setYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear 方法"
  - "Year 方法"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear 方法 (日期) (JavaScript)
設定 `Date` 物件中的年份值。  
  
## 語法  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numYear`  
 必要項。  如果年份介於 1900 到 1999 之間，這是等於年份減 1900 的數值。  如果是前述範圍以外的日期，則會是 4 位數的數值。  
  
## 備註  
 這個方法已不再使用，提供的目的只是為了回溯相容性 \(Backward Compatibility\)。  請改用 `setFullYear` 方法。  
  
 若要將 `Date` 物件的年份設成 1997，請呼叫 **setYear\(97\)**。  若要將年份設成 2010，則呼叫 **setYear\(2010\)**。  最後，若要將年份設成介於 0 到 99 的範圍內的年份，請使用 `setFullYear` 方法。  
  
> [!NOTE]
>  在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 1.0 版中，無論年份值為何，`setYear` 使用的值都是 `numYear` 的年份值加上 1900 的結果。  例如，將年份設定為 1899 時，`numYear` 就是 \-1，而年份為 2000 時 `numYear` 則是 100。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getFullYear 方法 \(日期\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(日期\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear 方法 \(日期\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(日期\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)