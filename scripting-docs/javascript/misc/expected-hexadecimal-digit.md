---
title: "必須是十六進位數 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 必須是十六進位數
您建立了不正確的 Unicode 逸出序列。  Unicode 逸出序列以 \\u 為開頭，後面緊接著四個十六進位數字 \(不多也不少\)。  Unicode 十六進位數字只能包含 0\-9 的數字、大寫字母 A\-F 及小寫字母 a\-f。  下列範例示範正確格式的 Unicode 逸出序列。  
  
```javascript  
z = "\u1A5F";  
```  
  
### 若要更正這個錯誤  
  
-   請確定您的 Unicode 十六進位數字是以 \\u 為開頭，而且只包含 0\-9 的數字、大寫字母 A\-F 和小寫字母 a\-f，並且分成四個數字。  
  
    > [!NOTE]
    >  如果您要在字串中使用常值文字 \\u，請使用兩個反斜線 \- \(\\\\u\) \- 第二個反斜線是為了逸出第一個反斜線。  
  
## 請參閱  
 [資料類型](../../javascript/data-types-javascript.md)