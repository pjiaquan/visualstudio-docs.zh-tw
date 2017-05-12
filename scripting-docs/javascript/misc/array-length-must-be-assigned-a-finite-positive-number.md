---
title: "陣列長度必須被指定為一有限的正值 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 陣列長度必須被指定為一有限的正值
設定現有 **Array** 物件的 **length** 屬性時，您指定了不是正數或零的陣列長度。  當您將值指派給 `Array` 物件的 **length** 屬性，而且該物件為負數或者不是數字 \(`NaN`\) 時，就會發生這個錯誤。  請注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將小數值自動轉換為整數。  
  
### 若要更正這個錯誤  
  
-   請指派正整數給 length 屬性。  陣列的大小並沒有上限，但是請勿超過最大整數值 \(大約 40 億\)。  下列範例示範設定 **Array** 物件之 **length** 屬性的正確方式。  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## 請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)