---
title: "CA1028：列舉儲存區應該是 Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1028：列舉儲存區應該是 Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用列舉型別的基礎型別不是 <xref:System.Int32?displayProperty=fullName>。  
  
## 規則描述  
 列舉型別是一種實值型別 \(Value Type\)，用以定義一組相關的具名常數。  根據預設，<xref:System.Int32?displayProperty=fullName> 資料型別會用於儲存常數值。  雖然您可以變更這個基礎型別，但是大多數案例中仍不需要或不建議進行變更。  請注意，使用小於 <xref:System.Int32> 的資料型別，無法有效改善效能。  如果您無法使用預設資料型別，應該使用其中一個符合 Common Language System \(CLS\) 標準的整數類資料型別 \(Integral Type\)、<xref:System.Byte>、<xref:System.Int16>、<xref:System.Int32> 或 <xref:System.Int64>，以確定所有的列舉值都可在符合 CLS 標準的程式語言中表示。  
  
## 如何修正違規  
 若要修正此規則的違規情形，除非有大小或相容性的問題，否則請使用 <xref:System.Int32>。  針對 <xref:System.Int32> 未大到可以儲存值的狀況，請使用 <xref:System.Int64>。  如果回溯相容性 \(Backward Compatibility\) 需要較小的資料型別，請使用 <xref:System.Byte> 或 <xref:System.Int16>。  
  
## 隱藏警告的時機  
 只有在回溯相容性問題需要這樣做時，才需隱藏這項規則的警告。  在應用程式中，無法遵守這項規則通常不會產生問題。  在需要語言互通性 \(Interoperability\) 的程式庫中，無法遵守這項規則可能會對使用者產生不良影響。  
  
## 違規範例  
  
### 描述  
 下列範例會顯示沒有使用建議之基礎資料型別的兩個列舉型別。  
  
### 程式碼  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## 修正方式範例  
  
### 描述  
 下列範例會藉由變更基礎資料型別為 <xref:System.Int32> 來修正上述違規。  
  
### 程式碼  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## 相關規則  
 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## 請參閱  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>