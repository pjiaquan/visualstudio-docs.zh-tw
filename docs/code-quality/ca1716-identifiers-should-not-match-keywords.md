---
title: "CA1716：識別項名稱不應該和關鍵字相符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1716：識別項名稱不應該和關鍵字相符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 命名空間、型別、虛擬成員或介面成員的名稱符合程式語言中的保留關鍵字。  
  
## 規則描述  
 命名空間、型別、虛擬成員及介面成員的識別項不應該符合以 Common Language Runtime 為目標之語言所定義的關鍵字。  視使用的語言和關鍵字而定，編譯器錯誤和模稜兩可 \(Ambiguity\) 會使程式庫變得難以使用。  
  
 這個規則會檢查下列語言中的關鍵字：  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 對於 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 關鍵字會使用不區分大小寫比較，對其他語言則會使用區分大小寫比較。  
  
## 如何修正違規  
 選取沒有出現在關鍵字清單中的名稱。  
  
## 隱藏警告的時機  
 如果您相信識別項不會造成使用者對 API 的混淆，以及程式庫可在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中以所有可用的語言來使用，則可以隱藏這項規則的警告。