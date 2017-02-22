---
title: "CA2208：請正確執行個體化引數例外狀況 | Microsoft Docs"
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
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208：請正確執行個體化引數例外狀況
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 可能原因包括下列狀況：  
  
-   對例外狀況型別為 \(或衍生自\) [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True) 的預設 \(無參數\) 建構函式進行呼叫。  
  
-   將錯誤的字串引數傳遞至例外狀況型別為 \(或衍生自\) [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True) 的參數化建構函式。  
  
## 規則描述  
 請呼叫其中一個可以提供更有意義之例外狀況 \(Exception\) 訊息的建構函式多載，而不呼叫預設建構函式。  例外狀況訊息應以程式開發人員為目標對象，清楚說明錯誤情況以及如何修正和避免例外狀況。  
  
 <xref:System.ArgumentException> 與衍生型別 \(Derived Type\) 之建構函式 \(由一個和兩個字串組成\) 的簽章在 `message` 和 `paramName` 參數部分不一致。  請確定這些建構函式是以正確的字串引數呼叫。  簽章如下：  
  
 <xref:System.ArgumentException> \(字串 `message`\)  
  
 <xref:System.ArgumentException>\(字串 `message` 和 `paramName`\)  
  
 <xref:System.ArgumentNullException> \(字串 `paramName`\)  
  
 <xref:System.ArgumentNullException> \(字串 `paramName` 和 `message`\)  
  
 <xref:System.ArgumentOutOfRangeException> \(字串 `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException> \(字串 `paramName` 和 `message`\)  
  
 <xref:System.DuplicateWaitObjectException> \(字串 `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException> \(字串 `parameterName` 和 `message`\)  
  
## 如何修正違規  
 若要修正此規則的違規情形，請呼叫接受訊息、參數或兩者都接受的建構函式，並確定所呼叫之 <xref:System.ArgumentException> 型別的引數是正確的。  
  
## 隱藏警告的時機  
 只有當參數型建構函式是以正確的字串引數呼叫時，您才可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例示範以錯誤方式產生 ArgumentNullException 型別之執行個體的建構函式。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## 範例  
 下列範例會切換建構函式引數以修正以上違規。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]