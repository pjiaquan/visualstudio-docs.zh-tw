---
title: "CA1809：避免使用過多區域變數 | Microsoft Docs"
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
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1809：避免使用過多區域變數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 成員包含 64 個以上的區域變數，其中有部分可能是編譯器產生的。  
  
## 規則描述  
 常見的效能最佳化作法是在處理器暫存器中儲存值，而非記憶體，這稱為「*註冊*」\(Enregistering\) 值。  Common Language Runtime 最多可註冊 64 個區域變數。  沒有註冊的變數會放在堆疊上，且在處理前必須先移至暫存器。  若要讓所有區域變數都有機會註冊，請將區域變數的數目限制為 64。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將實作重構為使用 64 個以內的區域變數。  
  
## 隱藏警告的時機  
 如果效能並非考量重點，則您可以放心地隱藏這項規則的警告，或是停用該規則。  
  
## 相關規則  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)