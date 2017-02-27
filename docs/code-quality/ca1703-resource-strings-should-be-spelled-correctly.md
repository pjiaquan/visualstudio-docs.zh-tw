---
title: "CA1703：資源字串應該拼寫正確 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703：資源字串應該拼寫正確
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。  
  
## 規則描述  
 此規則會將資源字串剖析成多個字 \(語彙基元化複合字\)，並檢查每個字\/語彙基元 \(Token\) 的拼寫是否正確。  如需剖析演算法的詳細資訊，請參閱[CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 預設會使用英文 \(en\) 版的拼字檢查程式。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用拼寫正確的單字，或是將單字加入自訂字典中。  如需如何使用自訂字典的詳細資訊，請參閱[CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  拼寫正確的單字可以縮短學習新軟體程式庫的時間。  
  
## 相關規則  
 [CA1701：資源字串複合字應該使用正確的大小寫](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)