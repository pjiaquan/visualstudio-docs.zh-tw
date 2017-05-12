---
title: "標記陳述式 (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue 陳述式"
  - "識別項, 陳述式"
  - "labeled 陳述式"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 標記陳述式 (JavaScript)
提供陳述式的識別項。  
  
## 語法  
  
```  
  
      label :  
   statements   
```  
  
## 參數  
 *label*  
 必要項。  參考標記陳述式 \(Label Statement\) 時使用的唯一識別項。  
  
 `statements`  
 選擇項。  與 *label* 有關的一個或多個陳述式。  
  
## 備註  
 **break** 和 **continue** 陳述式可以利用標記，指定要將 **break** 和 **continue** 套用至哪個陳述式。  
  
## 範例  
 在下列程式碼中，**continue** 陳述式會參考前面有 `Inner:` 陳述式的 **for** 迴圈。  當 `j` 為 24 時，**continue** 陳述式會讓該 **for** 迴圈進入下一個反覆運算。  每一行都會列印 21 到 23 以及 25 到 30 的數字。  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)