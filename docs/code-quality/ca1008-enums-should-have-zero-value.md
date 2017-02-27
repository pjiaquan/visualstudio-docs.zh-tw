---
title: "CA1008：列舉值中應該要有值為零的成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1008：列舉值中應該要有值為零的成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|分類|Microsoft.Design|  
|中斷變更|非中斷 \- 當提示您要將 **None** 值加入至沒有旗標的列舉時。中斷 \- 當提示您要重新命名或移除任何列舉值時。|  
  
## 原因  
 未套用 <xref:System.FlagsAttribute?displayProperty=fullName> 的列舉不定義含零值的成員；已套用 <xref:System.FlagsAttribute> 的列舉會定義含零值但名稱不為 'None' 的成員，或是列舉會定義多個值為零的成員。  
  
## 規則描述  
 就像其他實值型別一樣，未初始化的列舉其預設值為零。  非旗標屬性的列舉應該要定義含有零值的成員，使列舉可以指定有效的預設值。  如果合適，請將零值的成員命名為 'None'。  否則，請指派零給最常用的成員。  請注意，如果未在宣告中設定第一個列舉成員的值，其值預設為零。  
  
 如果在已套用 <xref:System.FlagsAttribute> 的列舉型別中定義零值成員，則其名稱應該是 'None'，以做為使用列舉型別並且未設定任何值時的預設值。  基於任何其他目的，使用零值成員會與 <xref:System.FlagsAttribute> 的用法相反，所以零值成員與 AND 和 OR 位元 \(Bitwise\) 運算子無法同時與其他成員一起使用。  這意味著只應該指派零值給一個成員。  請注意，如果在旗標屬性列舉中有多個成員具有零值，則 `Enum.ToString()` 將針對不是零的成員傳回不正確的結果。  
  
## 如何修正違規  
 若要對非旗標屬性列舉修正此規則的違規情形，請定義含有零值的成員。這是非中斷變更。  對於定義零值成員的旗標屬性列舉，將這個成員命名為 'None'，然後刪除任何其他含有零值的成員，這是需要中斷的變更。  
  
## 隱藏警告的時機  
 除了先前所提供的旗標屬性列舉型別之外，請勿隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示兩個滿足規則的列舉，以及一個違反規則的列舉 \(`BadTraceOptions`\)。  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## 相關規則  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 請參閱  
 <xref:System.Enum?displayProperty=fullName>