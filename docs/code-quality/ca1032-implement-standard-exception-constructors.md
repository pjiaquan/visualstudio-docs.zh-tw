---
title: "CA1032：必須實作標準例外狀況建構函式 | Microsoft Docs"
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
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1032：必須實作標準例外狀況建構函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 型別會擴充 <xref:System.Exception?displayProperty=fullName> 且未宣告所有必要的建構函式。  
  
## 規則描述  
 例外狀況類型必須實作下列建構函式：  
  
-   public NewException\(\)  
  
-   public NewException\(string\)  
  
-   public NewException\(string, Exception\)  
  
-   protected 或 private NewException\(SerializationInfo, StreamingContext\)  
  
 無法提供整組的建構函式會導致難以正確地處理例外狀況。  例如，具有 `NewException(string, Exception)` 簽章的建構函式會用於建立其他例外狀況所造成的例外狀況。  在沒有此建構函式的情況下，您就無法建立並擲回包含內部 \(巢狀\) 例外狀況的自訂例外狀況執行個體，這是 Managed 程式碼在這種情況下應進行的作業。  依照慣例，前三個例外狀況建構函式為公用的 \(Public\)。  第四個建構函式在非密封類別中是受保護的，而在密封類別中則是私用的。  如需詳細資訊，請參閱[CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將遺漏的建構函式加入至例外狀況，並確定這些建構函式具有正確的存取範圍。  
  
## 隱藏警告的時機  
 當違規是由於使用公用建構函式的不同存取層級所造成時，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例包含違反此規則的例外狀況類型，以及正常實作的例外狀況類型。  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]