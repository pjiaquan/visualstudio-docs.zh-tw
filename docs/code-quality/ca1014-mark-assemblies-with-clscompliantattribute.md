---
title: "CA1014：以 CLSCompliantAttribute 標記組件 | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014：以 CLSCompliantAttribute 標記組件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 組件沒有套用 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 屬性 \(Attribute\)。  
  
## 規則描述  
 Common Language Specification \(CLS\) 會定義命名限制、資料型別及組件必須遵守的規則 \(如果組件會使用於跨程式設計語言時\)。  良好的設計會要求所有組件使用 <xref:System.CLSCompliantAttribute> 明確表示 CLS 標準的符合性。  如果該屬性未出現於組件中，則表示組件不符合 CSL 標準。  
  
 符合 CLS 標準的組件可能會包含不符合標準的型別或型別成員。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將屬性加入至組件。  與其將整個組件標示為不符合標準，您應該判斷哪個型別或哪些型別成員不符合標準，然後將這些項目標示為不符合標準。  如果可能，您應該提供符合 CLS 標準的成員代替不符合標準的成員，以便讓最廣泛的可能使用者可以存取組件的所有功能。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  如果您不想讓組件為相容的，請套用此屬性並將其值設為 `false`。  
  
## 範例  
 下列範例會顯示已套用 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 屬性，並將其宣告為符合 CLS 標準的組件。  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## 請參閱  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)