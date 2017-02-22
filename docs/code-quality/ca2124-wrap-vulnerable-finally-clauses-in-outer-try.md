---
title: "CA2124：必須將有弱點的 finally 子句包裝在外層 try 中 | Microsoft Docs"
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
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124：必須將有弱點的 finally 子句包裝在外層 try 中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|分類|Microsoft.Security|  
|中斷變更|不中斷|  
  
## 原因  
 在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 1.0 和 1.1 版中，公用或保護的方法會包含 `try`\/`catch`\/`finally` 區塊。  `finally` 區塊似乎會重設安全性狀態，而且不會封入 `finally` 區塊中。  
  
## 規則描述  
 此規則會在以 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 1.0 和 1.1 版為目標的程式碼中找出 `try`\/`finally` 區塊，這些區塊可能很容易遭受呼叫堆疊中出現之惡意例外狀況篩選條件的攻擊。  如果在 try 區塊中發生敏感作業 \(例如模擬\) 並且擲回例外狀況，則可以在 `finally` 區塊之前執行篩選條件。  若是模擬範例，則表示篩選條件會以模擬的使用者執行。  篩選條件目前只能在 Visual Basic 中實作。  
  
> [!WARNING]
>  **注意**在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 \(含\) 以後版本中，如果直接在包含例外狀況區塊的方法中進行重設，執行階段會自動保護 `try`\/`catch`\/ `finally` 區塊，避免惡意例外篩選器干擾。  
  
## 如何修正違規  
 請將未包裝的 `try`\/`finally` 放置在外層 try 區塊中。  請參閱以下的第二個範例。  這會強制 `finally` 在篩選程式碼之前先執行。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 虛擬程式碼範例  
  
### 描述  
 下列虛擬程式碼會說明這項規則偵測到的模式。  
  
### 程式碼  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## 範例  
 下列虛擬程式碼會顯示您可以用於保護程式碼並符合此規則的模式。  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```