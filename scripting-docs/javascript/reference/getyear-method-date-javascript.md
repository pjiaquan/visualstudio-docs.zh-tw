---
title: "getYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，傳回年份"
  - "GetYear 方法"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear 方法 (日期) (JavaScript)
取得 `Date` 物件中的年份。  
  
## 語法  
  
```  
  
dateObj.getYear()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回年份。  
  
## 備註  
  
> [!IMPORTANT]
>  這個方法已過期的目的只是為了回溯相容性。  請改用 `getFullYear` 方法。  
  
 在 [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]，然後在開始 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]的 Internet Explorer 版本，則傳回值為減 1900 年的儲存年份。  例如，1899 年會傳回 \-1，而 2000 年則傳回 100。  
  
 在 [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] 傳遞 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]公式，決定年份。  1900 年到 1999，則傳回值為減 1900 年的儲存年份的 2 位數值。  對於日期範圍的外部，位數的年份就會傳回。  例如， 1996 年會傳回 96，而 1825 和 2025，則會傳回。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getFullYear 方法 \(日期\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(日期\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(日期\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear 方法 \(日期\)](../../javascript/reference/setyear-method-date-javascript.md)