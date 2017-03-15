---
title: "CA1017：以 ComVisibleAttribute 標記組件 | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017：以 ComVisibleAttribute 標記組件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 組件沒有套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 屬性 \(Attribute\)。  
  
## 規則描述  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性會判斷 COM 用戶端如何存取 Managed 程式碼。  良好的設計會要求組件明確表示 COM 的可視性。  COM 的可視性可以針對整個組件進行設定，然後針對個別型別及型別成員進行覆寫。  如果屬性不存在，則 COM 用戶端可以看到組件的內容。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將屬性加入至組件。  如果您不想讓 COM 用戶端看到組件，請套用屬性並將值設為 `false`。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  如果您想讓組件看得見，請套用屬性並將值設為 `true`。  
  
## 範例  
 下列範例會顯示已套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性，以防止 COM 用戶端看到的組件。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [限定互通的 .NET 類型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)