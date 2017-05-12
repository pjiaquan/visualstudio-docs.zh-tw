---
title: "use strict 指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "strict 模式"
  - "use strict 指示詞"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# use strict 指示詞
限制使用 JavaScript 中的某些功能。  只在 Internet Explorer 10 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式中支援。  
  
## 語法  
  
```javascript  
use strict  
```  
  
## 備註  
  
## 範例  
 下列程式碼會產生語法錯誤，因為在 strict 模式下必須以 `var` 宣告所有變數。  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## 請參閱  
 [strict 模式](../../javascript/advanced/strict-mode-javascript.md)