---
title: "屬性不可以宣告為 &#39;&lt;屬性修飾詞&gt;&#39;，因為它包含 &#39;Private&#39; 存取子。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性不可以宣告為 &#39;&lt;屬性修飾詞&gt;&#39;，因為它包含 &#39;Private&#39; 存取子。
屬性與 `Private` 屬性程序 \(`Get` 或 `Set`\) 標示為 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)。  
  
 如果基底類別屬性或程序宣告為[Private](/dotnet/visual-basic/language-reference/modifiers/private)，衍生的類別就不能覆寫該屬性或程序，因為無法存取它。 因此，您無法搭配 `Overridable` 使用 `Private`。 這不僅適用於屬性本身，也適用於個別的屬性程序。  
  
 **錯誤識別碼：**BC31108  
  
### 更正這個錯誤  
  
-   移除 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) 的 `Overridable` 關鍵字，或移除 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) 或 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) 的 `Private` 關鍵字。  
  
## 請參閱  
 [屬性程序](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)