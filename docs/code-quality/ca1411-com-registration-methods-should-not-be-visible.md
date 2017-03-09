---
title: "CA1411：COM 註冊方法不應該為可見的 | Microsoft Docs"
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
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411：COM 註冊方法不應該為可見的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 以 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性 \(Attribute\) 所標記的方法為外部可見的。  
  
## 規則描述  
 以元件物件模型 \(COM\) 註冊組件時，項目會加入至組件中每個 COM 可見型別的登錄。  在註冊和移除註冊程序中，會分別呼叫以 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 和 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 屬性標記的方法，以便執行這些型別之註冊\/移除註冊特定的使用者程式碼。  不得在這些處理序之外呼叫此程式碼。  
  
## 如何修正違規  
 若要修正這項規則的違規情形，請將方法的存取範圍變更為 `private` 或 `internal` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Friend`\)。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的兩個方法。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## 相關規則  
 [CA1410：應該符合 COM 註冊方法](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 註冊組件](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)