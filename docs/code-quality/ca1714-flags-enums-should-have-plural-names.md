---
title: "CA1714：旗標列舉應該使用複數名稱 | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714：旗標列舉應該使用複數名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 公用的 \(Public\) 列舉型別 \(Enumeration\) 具有 <xref:System.FlagsAttribute?displayProperty=fullName>，而且其名稱不能以 's' 做結尾。  
  
## 規則描述  
 以 <xref:System.FlagsAttribute> 標記的型別擁有複數形的名稱，因為這個屬性表示可以指定一個以上的值。  例如，定義該星期之天數的列舉型別可能適用於可以指定不只一天的應用程式。  這個列舉型別應該有 <xref:System.FlagsAttribute>，而其名稱可能是 'Days'。  只能指定一天的類似列舉型別不會有這個屬性，而且名稱可能是 'Day'。  
  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
## 如何修正違規  
 請將列舉型別的名稱變成複數詞，而如果不可同時指定多個列舉值，則請移除 <xref:System.FlagsAttribute> 屬性。  
  
## 隱藏警告的時機  
 如果名稱是複數詞但不是以 's' 結尾，您可以放心地隱藏違規。  例如，如果前述的多天列舉名稱為 'DaysOfTheWeek'，雖然這違反了規則的邏輯，但卻不是它的意圖。  這種違規應該隱藏起來。  
  
## 相關規則  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 請參閱  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [列舉設計](../Topic/Enum%20Design.md)