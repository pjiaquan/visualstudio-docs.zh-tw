---
title: "陣列長度必須是一有限的正整數 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 陣列長度必須是一有限的正整數
您呼叫 **Array** 建構函式時使用的引數並非整數 \(整數包含零以及正整數\)。  
  
### 若要更正這個錯誤  
  
-   請只用正整數建立新的 `Array` 物件。  如果在您要建立只有一個元素的陣列，並且該元素不是整數，請分成兩個步驟來建立。  首先建立只有一個元素的陣列，然後設定第一個元素 \(array\[0\]\) 的值。  下列範例會產生這個錯誤。  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     下列範例會示範正確的方式，指定只有一個數值元素的陣列。  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     陣列的大小並沒有上限，但是請勿超過最大整數值 \(大約 40 億\)。  
  
## 請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)