---
title: "CA1410：應該符合 COM 註冊方法 | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410：應該符合 COM 註冊方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 型別會宣告利用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性 \(Attribute\) 所標記的方法，但不會宣告利用 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性所標記的方法 \(反之亦然\)。  
  
## 規則描述  
 若要使用元件物件模型 \(COM\) 用戶端建立 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 型別，必須先註冊該型別。  如果它可以使用，則會在註冊過程期間呼叫利用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 屬性所標記的方法，以執行使用者指定的程式碼。  在移除註冊處理序期間，呼叫利用 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 屬性所標記的對應方法，取消註冊方法的作業。  
  
## 如何修正違規  
 若要修正這個規則的違規情形，請加入對應的註冊或移除註冊方法。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反規則的型別。  註解的程式碼會顯示違規的修正。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## 相關規則  
 [CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 註冊組件](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)