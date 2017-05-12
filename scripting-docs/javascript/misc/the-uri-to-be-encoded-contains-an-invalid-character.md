---
title: "要編碼的 URI 包含無效的字元 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 要編碼的 URI 包含無效的字元
您嘗試將字串編碼為 URI \(統一資源識別元\)，不過字串中包含無效的字元。  雖然要轉換為 URI 之字串中的大部分字元都是有效的，但是部分 Unicode 字元序列不合法。  
  
### 若要更正這個錯誤  
  
-   請確定要編碼的字串只包含有效的 Unicode 字元序列。  完整的 URI 是由一連串的元件和分隔符號組成。  角括弧內的名稱代表元件，而 ":"、"\/"、";" 和 "?" 是用來當做分隔符號的保留字元。  一般的形式是：  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## 請參閱  
 [encodeURI 函式](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函式](../../javascript/reference/encodeuricomponent-function-javascript.md)