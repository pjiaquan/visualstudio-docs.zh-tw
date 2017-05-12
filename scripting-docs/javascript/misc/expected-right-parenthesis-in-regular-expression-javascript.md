---
title: "在規則運算式中必須是 &#39;)&#39; (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 在規則運算式中必須是 &#39;)&#39; (JavaScript)
您嘗試建立規則運算式的擷取內容、判斷提示或群組，但是未包含右括弧。  在規則運算式中，括弧有數種用途，  主要是用來擷取子運算式、指定判斷提示，或是將模式分組讓 \*、\+ 和 ? 等符號能將多個項目視為一個單位。  
  
### 若要更正這個錯誤  
  
-   請加上最右邊的右括弧。  
  
    > [!NOTE]
    >  如果您希望比對單一括弧，請使用反斜線 \(\\\) 逸出該括弧，如此 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就不會將其解譯為特殊字元。  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)