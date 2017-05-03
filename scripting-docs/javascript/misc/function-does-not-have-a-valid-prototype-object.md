---
title: "函式沒有有效的原型物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 函式沒有有效的原型物件
您嘗試使用 **instanceof** 來判斷物件是否衍生自特殊的函式類別，但是您將物件的 `prototype` 屬性重新定義為 `null` 或外部物件型別 \(兩者都不是有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件\)。  外部物件可以是主應用程式物件模型的物件 \(例如，Internet Explorer 的文件或視窗物件\) 或者是外部 COM 物件。  
  
### 若要更正這個錯誤  
  
-   請確定此函式的 `prototype` 屬性會參考有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  
  
## 請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)