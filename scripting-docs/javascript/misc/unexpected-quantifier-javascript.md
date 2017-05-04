---
title: "非預期的數量詞 (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 非預期的數量詞 (JavaScript)
當您撰寫規則運算式搜尋模式時，您使用了不合法的重複因數建立模式元素。  例如，以下  
  
```  
/^+/  
```  
  
 模式不合法，因為元素 ^ \(輸入開頭\) 不得有重複因數。  下表列出不得有重複因數的元素。  
  
|元素|描述|  
|--------|--------|  
|^|輸入開頭|  
|$|輸入結尾|  
|\\b|字緣|  
|\\B|非字緣|  
|\*|零個或多個重複|  
|\+|一個或多個重複|  
|?|零個或一個重複|  
|{n}|n 個重複|  
|{n,}|n 個或多個重複|  
|{n,m}|從 n 到 m 個重複 \(包含頭尾\)|  
  
### 若要更正這個錯誤  
  
-   確定您的搜尋模式元素只包含合法的重複因數。  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)