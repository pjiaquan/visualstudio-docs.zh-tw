---
title: "在規則運算式中必須是 &#39;]&#39; (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 在規則運算式中必須是 &#39;]&#39; (JavaScript)
您嘗試建立用於規則運算式比對的字元類別，但是卻遺漏右方括弧。  用方括弧括住個別的常值字元組合，就能將它們組合成字元類別。  字元類別會針對內含的字元逐一進行比對。  例如，內含字元為 \/\[abc\]\/，則 "a"、"b" 或 "c" 都屬於比對符合的字母。  
  
### 若要更正這個錯誤  
  
-   將右方括弧加入至規則運算式。  
  
    > [!NOTE]
    >  如果您希望比對單一方括弧，請使用反斜線逸出該方括弧 \(例如 \\\[\)，如此 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就不會將其解譯為特殊字元。  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)