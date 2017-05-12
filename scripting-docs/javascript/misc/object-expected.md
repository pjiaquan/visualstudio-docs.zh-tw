---
title: "必須是物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5007"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 必須是物件
您嘗試對非 `Object` 類型的物件叫用方法或屬性，或在需要 `Object` 時傳遞非 `Object` 類型的引數。  
  
### 更正這個錯誤  
  
-   只能對 `Object` 類型的物件叫用方法或屬性。  
  
-   如果非物件引數發生錯誤，請傳遞 `Object` 類型的物件。  
  
-   確認是否叫用未定義或 Null 參考，而非 `Object` 類型的物件。  
  
     例如，如果您針對下列程式碼中的 myVar 收到這個錯誤：  
  
    ```javascript  
    var str = myVar.toString();  
    ```  
  
     您可以改用此程式碼：  
  
    ```javascript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## 請參閱  
 [Object 物件](../../javascript/reference/object-object-javascript.md)   
 [物件和陣列](../../javascript/objects-and-arrays-javascript.md)