---
title: "CA1019：必須定義屬性引數的存取子 | Microsoft Docs"
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
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019：必須定義屬性引數的存取子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 在它的建構函式 \(Constructor\) 中，屬性 \(Attribute\) 所定義的引數沒有對應的屬性 \(Property\)。  
  
## 規則描述  
 屬性可以定義必須在將屬性套用至目標時指定的強制引數。  這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。  對於每個強制引數而言，屬性 \(Attribute\) 還須提供對應的唯讀屬性 \(Property\)，才可以在執行時期擷取引數值。  此規則會檢查每個建構函式參數，以查看您是否已為它們定義對應的屬性。  
  
 屬性也可以定義選擇性引數，也稱為具名引數。  這些引數會依照名稱提供給屬性 \(Attribute\) 建構函式，且必須有對應的讀取\/寫入屬性 \(Property\)。  
  
 對於強制和選擇性引數而言，對應的屬性和建構函式參數應使用相同的名稱，但大小寫不同。  屬性會採用 Pascal 命名法的大小寫慣例，而參數則會採用 Camel 命名法的大小寫慣例。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請替沒有唯讀屬性的每個建構函式參數加入唯讀屬性。  
  
## 隱藏警告的時機  
 如果您不希望強制引數的值是可以擷取的，則請隱藏這項規則的警告。  
  
## 自訂屬性範例  
  
### 描述  
 下列範例所顯示的兩個屬性會定義強制 \(位置\) 參數。  第一個屬性實作的定義不正確。  第二個實作則是正確的。  
  
### 程式碼  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## 位置和具名引數  
  
### 描述  
 位置和具名引數是用來讓您程式庫的消費者，分清楚哪些引數對屬性是強制的，而哪些是選擇性的。  
  
 下列範例顯示同時具有位置和具名引數的屬性實作。  
  
### 程式碼  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### 註解  
 下列範例顯示如何套用自訂屬性 \(Attribute\) 到兩個屬性 \(Property\)：  
  
### 程式碼  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## 相關規則  
 [CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 請參閱  
 [屬性](../Topic/Attributes1.md)