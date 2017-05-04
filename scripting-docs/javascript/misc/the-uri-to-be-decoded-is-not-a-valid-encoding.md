---
title: "要解碼的 URI 不是有效的編碼 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 要解碼的 URI 不是有效的編碼
您嘗試解碼格式不正確的「統一資源識別項」\(Uniform Resource Identifier，URI\)。  URI 有特殊的語法，在 URI 中使用非英數字元前，大部分都必須先經過編碼。  您可以使用 `encodeURI` 和 `encodeURIComponent` 方法，將一般 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字串編碼成 URI。  
  
 完整的 URI 是由一連串的元件和分隔符號組成。  一般的形式是：  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 角括弧內的名稱代表元件，而 ":"、"\/"、";" 和 "?" 是用來當做分隔符號的保留字元。  
  
### 若要更正這個錯誤  
  
-   確定您只解碼有效的 URI。  因為一般 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 字串可能包含無效的字元，所以您無法解碼這些字串。  
  
## 請參閱  
 [decodeURI 函式](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函式](../../javascript/reference/decodeuricomponent-function-javascript.md)