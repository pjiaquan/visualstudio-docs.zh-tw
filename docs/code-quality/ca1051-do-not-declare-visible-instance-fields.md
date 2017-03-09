---
title: "CA1051：不要宣告可見的執行個體欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051：不要宣告可見的執行個體欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的型別具有外部可見的執行個體 \(Instance\) 欄位。  
  
## 規則描述  
 欄位的主要用法應該是當做實作詳細資料。  欄位應該是 `private` 或 `internal`，而且應使用屬性公開 \(Expose\)。  存取屬性與存取欄位一樣容易，而且屬性存取子 \(Accessor\) 中的程式碼可隨著型別的功能展開而變更，而不須採用中斷變更。  剛傳回私用或內部欄位值的屬性已進行最佳化，以便與存取欄位一樣地執行。使用外部可見的欄位，對於屬性的效能提升毫無關聯。  
  
 外部可見是指 `public`、`protected` 和 `protected internal` \(在 Visual Basic 中為 `Public`、`Protected` 和 `Protected Friend`\) 存取範圍層級。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使欄位成為 `private` 或 `internal`，並且使用外部可見的屬性予以公開。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  外部可見的欄位所提供的優點都可以供屬性使用。  此外，[Link Demands](../Topic/Link%20Demands.md)不會保護公用欄位。  請參閱 [CA2112：受保護類型不應公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。  
  
## 範例  
 下列範例會示範違反此規則的型別 \(`BadPublicInstanceFields`\)。  `GoodPublicInstanceFields` 會顯示修正過的程式碼。  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## 相關規則  
 [CA2112：受保護類型不應公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## 請參閱  
 [Link Demands](../Topic/Link%20Demands.md)