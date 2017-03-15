---
title: "CA1720：識別項不應包含類型名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1720：識別項不應包含類型名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 外部可見成員中的參數名稱會包含資料型別名稱。  
  
 \-或\-  
  
 外部可見成員的名稱會包含語言專屬的資料型別名稱。  
  
## 規則描述  
 參數與成員名稱最好是用於傳達其意義，而不是說明預期將會由開發工具提供的型別。  如果必須使用資料型別名稱，成員名稱請使用和語言無關的名稱而不是語言專屬名稱。  例如，請使用和語言無關的資料型別名稱 Int32，而不是 C\# 型別名稱 'int'。  
  
 對於參數或成員名稱中的每個分離權杖，會使用不區分大小寫的方式，針對下列特定語言資料型別名稱進行檢查：  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   未簽署  
  
-   經過簽署  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 此外，對於參數的名稱也會使用不區分大小寫的方式，針對下列和語言無關的資料型別名稱進行檢查：  
  
-   物件  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   字串  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   指標  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## 如何修正違規  
 **如果針對參數引發：**  
  
 以更能有效描述其意義的詞彙，或是更泛型的詞彙 \(例如 'value'\) 取代參數名稱中的資料型別識別項。  
  
 **如果針對成員引發：**  
  
 以更能有效描述其意義的詞彙、和語言無關的對等用法，或是更泛型的詞彙 \(例如 'value'\) 取代成員名稱中的語言專屬資料型別識別項。  
  
## 隱藏警告的時機  
 偶爾使用以型別為基礎的參數與成員名稱可能很恰當。  但是對新的開發而言，在所有已知的案例中，您都不應該隱藏這項規則的警告。  對於之前隨附的程式庫，您可能必須隱藏這項規則的警告。  
  
## 相關規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：識別項不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719：參數名稱不應符合成員名稱](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)