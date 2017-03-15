---
title: "CA2221：完成項應該受到保護 | Microsoft Docs"
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
  - "CA2221"
  - "FinalizersShouldBeProtected"
helpviewer_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2221：完成項應該受到保護
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|FinalizersShouldBeProtected|  
|CheckId|CA2221|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 公用 \(Public\) 型別會實作未指定系列 \(protected\) 存取的完成項。  
  
## 規則描述  
 完成項必須使用系列存取修飾詞 \(Modifier\)。  C\#、Visual Basic 和 Visual C\+\+ 編譯器會強制使用此規則。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將完成項變更為可供系列存取。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 在任何高階 .NET 語言中不得違反此規則。若您正在寫入 Microsoft Intermediate Language，則可違反此規則。  
  
```  
// =============== CLASS MEMBERS DECLARATION ===================  
//   note that class flags, 'extends' and 'implements' clauses  
//          are provided here for information only  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance void  
            Finalize() cil managed  
    {  
  
      // Code size       1 (0x1)  
      .maxstack  0  
      IL_0000:  ret  
    } // end of method FinalizeMethodNotProtected::Finalize  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method FinalizeMethodNotProtected::.ctor  
  
  } // end of class FinalizeMethodNotProtected  
} // end of namespace  
```  
  
## 請參閱  
 [處置模式](../Topic/Dispose%20Pattern.md)