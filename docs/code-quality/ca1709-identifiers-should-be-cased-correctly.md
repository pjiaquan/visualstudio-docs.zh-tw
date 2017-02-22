---
title: "CA1709：識別項名稱應該使用正確的大小寫 | Microsoft Docs"
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
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1709：識別項名稱應該使用正確的大小寫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|分類|Microsoft.Naming|  
|中斷變更|中斷 \- 在組件、命名空間、型別、成員以及參數上引發時。<br /><br /> 非中斷 \- 在泛型型別參數上引發時。|  
  
## 原因  
 識別項名稱的大小寫有誤。  
  
 \-或\-  
  
 識別項的名稱包含兩個字母的縮略字，且第二個字母為小寫。  
  
 \-或\-  
  
 識別項的名稱會包含三個以上之大寫字母的縮略字。  
  
## 規則描述  
 命名慣例會為針對 Common Language Runtime 的程式庫提供通用的外觀。  如此可縮短新軟體程式庫的學習過程，並讓客戶深信程式庫是由學有專長的人員以不斷開發的 Managed 程式碼開發而成。  
  
 根據慣例，參數名稱是使用 Camel 命名法的大小寫慣例，而命名空間 \(Namespace\)、型別和成員名稱則使用 Pascal 命名法的大小寫慣例。  遵守 Camel 命名法之大小寫慣例的名稱，第一個字母為小寫，名稱中其他所有字的第一個字母則為大寫。  Camel 命名法的大小寫慣例範例有 "packetSniffer"、"ioFile" 和 "fatalErrorCode"。  遵守 Pascal 命名法之大小寫慣例的名稱，第一個字母為大寫，而名稱中其他所有字的第一個字母則為大寫。  Pascal 命名法之大小寫慣例的範例為 "PacketSniffer"、"IOFile" 和 "FatalErrorCode"。  
  
 此規則會根據大小寫將名稱分割為文字，並針對一般兩個字母的文字清單檢查所有兩個因英文字母的文字，如 "In" 或 "My"。  如果找不到符合項目，就會假設該文字為縮略字。  此外，這項規則也假設當資料列中的名稱包含四個大寫字母時，或是名稱尾端包含三個大寫字母時，找到的字就是縮略字。  
  
 依照慣例，兩個字母的縮略字會使用全大寫字母，而三個以上之字元的縮略字則會使用 Pascal 大小寫慣例。  下列範例會使用此命名慣例：'DB'、'CR'、'Cpa' 和 'Ecma'。  下列範例則違反此慣例：'Io'、'XML' 和 'DoD'，以及非參數名稱的 'xp' 和 'cpl'。  
  
 'ID' 是導致違反此規則的特殊大小寫。'Id' 不是縮略字，而是 'identification' 的縮寫。  
  
## 如何修正違規  
 請將名稱變更為正確的大小寫。  
  
## 隱藏警告的時機  
 如果有專屬的命名慣例，或是如果識別項表示適當的名稱，例如：公司名稱或技術，則可以安心隱藏這個警告。  
  
 您也可以將特定詞彙、縮寫和縮略字日至程式碼分析自訂字典。  在自訂字典中指定的詞彙不會造成對此規則的違規。  如需詳細資訊，請參閱[如何：自訂程式碼分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)。  
  
## 相關規則  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)