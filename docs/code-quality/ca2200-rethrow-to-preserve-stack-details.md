---
title: "CA2200：請重新擲回以保存堆疊詳細資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2200：請重新擲回以保存堆疊詳細資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 例外狀況 \(Exception\) 遭到重新擲回，而且已在 `throw` 陳述式 \(Statement\) 中明確指定此例外狀況。  
  
## 規則描述  
 一旦擲回例外狀況後，它所傳遞的部分資訊為堆疊追蹤。  此堆疊追蹤為方法呼叫階層的清單，以擲回例外狀況的方法為開頭，而以攔截例外狀況的方法為結尾。  如果例外狀況是透過在 `throw` 陳述式中指定例外狀況而重新擲回，則會在目前方法重新啟動堆疊追蹤，而在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單則會遺失。  若要保留含有例外狀況的原始堆疊追蹤資訊，請使用 `throw` 陳述式而不指定例外狀況。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請重新擲回例外狀況而不需明確指定例外狀況。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的方法 \(`CatchAndRethrowExplicitly`\)，以及符合規則的方法 \(`CatchAndRethrowImplicitly`\)。  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]