---
title: "CA1016：以 AssemblyVersionAttribute 標記組件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016：以 AssemblyVersionAttribute 標記組件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 組件沒有版本號碼。  
  
## 規則描述  
 組件的識別 \(Identity\) 是由下列資訊所構成：  
  
-   組件名稱  
  
-   版本號碼  
  
-   文化特性  
  
-   公開金鑰 \(適用於強式名稱組件\)  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的型別。  版本號碼會與版本和發行者 \(Publisher\) 原則一起使用。  應用程式預設只會與建置它們的組件版本一起執行。  
  
## 如何修正違規  
 若要修正此規則的違規，請使用 <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 屬性 \(Attribute\)，將版本號碼加入到組件。  請參閱下列範例。  
  
## 隱藏警告的時機  
 組件若是由協力廠商使用，或位於實際執行環境時，請勿隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示已套用 <xref:System.Reflection.AssemblyVersionAttribute> 屬性的組件。  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## 請參閱  
 [組件版本控制](../Topic/Assembly%20Versioning.md)   
 [如何：建立發行者原則](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)