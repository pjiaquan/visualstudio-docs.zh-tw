---
title: "CA1700：不要在列舉值名稱中包含 &#39;Reserved&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1700：不要在列舉值名稱中包含 &#39;Reserved&#39;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 列舉型別成員的名稱會包含 "reserved" 這個字。  
  
## 規則描述  
 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 \(Placeholder\)。  重新命名或移除成員是中斷變更。  您不應該預期使用者會只因成員名稱包含 "reserved" 就會忽略該成員，也不能依賴使用者讀取或遵守文件。  此外，由於保留的成員會出現在物件瀏覽器和智慧型整合式開發環境中，所以在不知道真正使用哪些成員的情況下，它們可能會導致混淆。  
  
 因此不是使用保留的成員，而是在未來版本將新的成員加入到列舉型別。  在大部分情況下，只要新成員的加入不會導致原始成員值的變更，則這個加入便不是中斷變更。  
  
 只有在某些情況下，即使原始成員仍然保持它的原始值，加入成員的作業仍是中斷變更。  主要是因為呼叫端在包含整個成員清單的傳回值，以及在預設情況下發生例外狀況的傳回值上使用 `switch` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Select`\)，若沒有中斷這個呼叫端，將無法從現有的程式碼路徑傳回新的成員。  其次是因為用戶端程式碼可能無法從反映 \(Reflection\) 方法 \(例如 <xref:System.Enum.IsDefined%2A?displayProperty=fullName>\) 處理行為中的變更。  因此，如果現有的方法必須傳回新成員，或已知的應用程式因為不良的反映使用方式而發生不相容，則唯一非中斷的解決方案就是：  
  
1.  新增包含原始和新成員的新列舉。  
  
2.  使用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性標示原始列舉。  
  
 對於任何公開 \(Expose\) 原始列舉型別的外部可見型別或成員，請遵循相同程序。  
  
## 如何修正違規  
 若要修正違反此規則的情形，請移除或重新命名該成員。  
  
## 隱藏警告的時機  
 對於目前所使用的成員或先前提供的程式庫，您可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)