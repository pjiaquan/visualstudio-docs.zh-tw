---
title: "CA1053：靜態預留位置類型不應包含建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1053：靜態預留位置類型不應包含建構函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或巢狀公用型別只宣告靜態成員，而且具有公用或保護的預設建構函式。  
  
## 規則描述  
 建構函式不是必要的，因為呼叫靜態成員不需型別的執行個體。  此外，因為型別沒有非靜態成員，因此建立執行個體不會提供任何型別成員的存取權限。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除預設建構函式或使它成為私用的。  
  
> [!NOTE]
>  如果型別並未定義任何建構函式，則有些編譯器會自動建立公用預設建構函式。  如果您的型別情況如此，請加入私用預設建構函式以排除此違規情形。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  出現建構函式意味著此型別不是靜態型別。  
  
## 範例  
 下列範例顯示違反此規則的型別。  請注意，原始程式碼中沒有預設建構函式。  當此程式碼編譯成組件 \(Assembly\) 時，C\# 編譯器將會插入違反此規則的預設建構函式。  若要更正此錯誤，請宣告私用建構函式。  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]