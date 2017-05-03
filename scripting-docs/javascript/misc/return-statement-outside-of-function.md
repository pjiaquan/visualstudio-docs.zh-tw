---
title: "函式外部的 &#39;return&#39; 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 函式外部的 &#39;return&#39; 陳述式
您在程式碼的全域範圍內使用了 `return` 陳述式。  `return` 陳述式只能在函式的主體內出現。  
  
 在運算式中，您可以使用函式名稱加上 `()` 運算子來叫用該函式。  所有運算式都有值，而 `return` 陳述式可用來指定函式要傳回的值。  一般的形式是：  
  
```  
  
return [ expression ];  
```  
  
 執行 `return` 陳述式時，運算式會在經過評估後當做函式的值傳回。  如果沒有運算式，則會傳回 **undefined** 值。  
  
 執行 `return` 陳述式時，即使函式主體內還有其他陳述式尚未執行，函式仍然會停止執行。  本規則的例外情形是如果在 **try** 區塊中使用 **return** 陳述式，並且也有對應的 **finally** 區塊，則在函式傳回之前會先執行 **finally** 區塊中的程式碼。  
  
 如果函式已執行到主體的結尾卻未執行 `return` 陳述式就傳回，表示傳回的是 **undefined** 值 \(這表示函式結果不可做為較大型運算式的一部分\)。  
  
### 若要更正這個錯誤  
  
-   從程式碼主體 \(全域範圍\) 移除 `return` 陳述式。  
  
## 請參閱  
 [return 陳述式](../../javascript/reference/return-statement-javascript.md)   
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [caller 屬性 \(函式\)](../../javascript/reference/caller-property-function-javascript.md)