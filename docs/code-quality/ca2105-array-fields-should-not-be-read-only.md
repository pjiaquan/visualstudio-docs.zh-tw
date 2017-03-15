---
title: "CA2105：陣列欄位不應為唯讀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2105：陣列欄位不應為唯讀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 儲存陣列的公用 \(Public\) 或保護 \(Protected\) 的欄位宣告為唯讀。  
  
## 規則描述  
 當您將 `readonly` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中是 `ReadOnly`\) 修飾詞套用至包含陣列的欄位時，欄位就不能變更為參考不同的陣列。  但是，儲存在唯讀欄位的陣列元素則可以變更。  根據可公開存取的唯讀陣列元素進行決策或執行作業的程式碼，可能會包含可利用的安全性弱點。  
  
 請注意，具有公用欄位也會違反設計規則[CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。  
  
## 如何修正違規  
 若要修正此規則所定義的安全性弱點，請勿依賴可公開存取的唯讀陣列內容。  強烈建議您使用下列其中一個程序：  
  
-   以無法變更的強型別 \(Strongly Typed\) 集合取代此陣列。  如需詳細資訊，請參閱<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>。  
  
-   以會傳回私用陣列複製品 \(Clone\) 的方法取代公用欄位。  因為您的程式碼並不依賴此複製品，因此修改元素就不會有危險。  
  
 如果您選擇第二種方式，請勿以屬性取代欄位，因為傳回陣列的屬性會對效能造成負面影響。  如需詳細資訊，請參閱[CA1819：屬性不應傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)。  
  
## 隱藏警告的時機  
 強烈建議您排除問題而不是移除規則警告項目。  幾乎在所有情況中，唯讀欄位的內容都很重要。  如果您也有相同的情況，則請移除 `readonly` 修飾詞，而非排除訊息。  
  
## 範例  
 下列會示範違反這項規則的危險性。  第一個部分會顯示具有型別 `MyClassWithReadOnlyArrayField` 的範例程式庫，其中包含兩個不安全的欄位 \(`grades` 和 `privateGrades`\)。  `grades` 為公用欄位，因此容易遭受任何呼叫端攻擊。  雖然 `privateGrades` 為私用欄位，但因它是由 `GetPrivateGrades` 方法傳回給呼叫端，所以仍易遭受攻擊。  `GetSecurePrivateGrades` 方法會以安全的方式公開 `securePrivateGrades` 欄位。  此欄位宣告為私用，並且在上述方法中會複製另一份實體將該欄位傳回，此法有遵循良好的設計法則。  第二個部分所顯示的程式碼會變更儲存在 `grades` 和 `privateGrades` 成員中的值。  
  
 下列範例中出現的範例類別庫。  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## 範例  
 下列程式碼會使用範例類別庫說明唯讀陣列的安全性問題。  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 本範例的輸出如下：  
  
  **在修改之前:階層:90， 90， 90 私人階層:90， 90， 90 安全性階層， 90， 90， 90。修改之後:階層:90， 555， 90 私人階層:90， 555， 90 安全性階層， 90， 90， 90。**   
## 請參閱  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>