---
title: "CA2204：常值必須使用正確的拼字 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204：常值必須使用正確的拼字
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 方法會將常値字串傳遞至需要當地語系化字串的參數或屬性中使用的字串，且常值字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。  
  
## 規則描述  
 此規則會檢查常值字串，當下列一或多個情形成立時，該字串會做為值傳遞至參數或屬性：  
  
-   參數或屬性 \(property\) 的 <xref:System.ComponentModel.LocalizableAttribute> 屬性 \(attribute\) 設定為 true。  
  
-   參數或屬性名稱包含「文字」、「訊息」或「標題」。  
  
-   傳遞至 Console.Write 或 Console.WriteLine 方法之字串參數的名稱為 "value" 或 "format"。  
  
 這個規則會將常值字串剖析成文字，將複合字 Token 化，然後檢查每個文字\/Token 的拼字。  如需剖析演算法的詳細資訊，請參閱[CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 預設會使用英文 \(en\) 版的拼字檢查程式。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請更正單字的拼寫，或是將單字加入自訂字典中。  如需如何使用自訂字典的詳細資訊，請參閱[如何：自訂程式碼分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  拼寫正確的單字可縮短新軟體程式庫所需的學習過程。  
  
## 相關規則  
 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703：資源字串應該拼寫正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)