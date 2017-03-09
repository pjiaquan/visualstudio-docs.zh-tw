---
title: "CA2102：在一般處理常式中攔截非 CLSCompliant 的例外狀況 | Microsoft Docs"
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
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102：在一般處理常式中攔截非 CLSCompliant 的例外狀況
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 組件 \(Assembly\) 中未標記 <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> 或已標記 `RuntimeCompatibility(WrapNonExceptionThrows = false)` 的成員包含可處理 <xref:System.Exception?displayProperty=fullName> 的 catch 區塊，而且未包含緊接在後面的一般 catch 區塊。  此規則會忽略 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 組件。  
  
## 規則描述  
 處理 <xref:System.Exception> 的 catch 區塊會攔截符合 Common Language Specification \(CLS\) 標準的所有例外狀況。  但是，它不會攔截不符合 CLS 標準的例外狀況。  不符合 CLS 標準的例外狀況可能從機器碼，或是從 Microsoft Intermediate Language \(MSIL\) 組譯工具產生的 Managed 程式碼擲回。  請注意，C\# 和 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器不允許擲回不符合 CLS 標準的例外狀況，而 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 則不會攔截不符合 CLS 標準的例外狀況。  如果 catch 區塊的目的是要處理所有的例外狀況，請使用下列一般 catch 區塊語法。  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` 或 `catch(Object^) {}`  
  
 當 catch 區塊移除了先前允許的使用權限時，未處理之不符合 CLS 標準的例外狀況將會變成安全性問題。  由於系統不會攔截不符合 CLS 標準的例外狀況，因此擲回不符合 CLS 標準之例外狀況的惡意方法可能使用提高的權限來執行。  
  
## 如何修正違規  
 若要在目的是攔截所有例外狀況時修正此規則的違規情形，請替換或加入一般 catch 區塊，或將組件標記為 `RuntimeCompatibility(WrapNonExceptionThrows = true)`。  如果 catch 區塊中移除了使用權限，請在一般 catch 區塊中複製功能。  如果您的目的不是要處理所有的例外狀況，請將處理 <xref:System.Exception> 的 catch 區塊取代成處理特定例外狀況類型的 catch 區塊。  
  
## 隱藏警告的時機  
 如果 try 區塊不包含任何可能產生不符合 CLS 標準之例外狀況的陳述式，則可以放心地隱藏這項規則的警告。  由於任何機器碼或 Managed 程式碼都有可能擲回不符合 CLS 標準的例外狀況，因此必須具備可在 try 區塊內所有程式碼路徑中執行之所有程式碼的知識。  請注意，Common Language Runtime 不會擲回不符合 CLS 標準的例外狀況。  
  
## 範例  
 下列範例顯示擲回不符合 CLS 標準之例外狀況的 MSIL 類別 \(Class\)。  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## 範例  
 下列範例顯示包含符合此規則之一般 catch 區塊的方法。  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 將前述範例編譯如下：  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## 相關規則  
 [CA1031：不要攔截一般例外狀況類型](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## 請參閱  
 [例外狀況和例外狀況處理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/zh-tw/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)