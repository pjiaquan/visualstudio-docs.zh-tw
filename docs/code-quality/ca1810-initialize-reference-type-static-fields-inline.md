---
title: "CA1810：必須初始化參考類型內部的靜態欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1810：必須初始化參考類型內部的靜態欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 參考型別會宣告明確的靜態建構函式。  
  
## 規則描述  
 當型別宣告明確的靜態建構函式時，Just\-In\-Time \(JIT\) 編譯器會將檢查加入至型別的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。  當存取任何靜態成員或建立型別的執行個體時，就會觸發靜態初始設定。  但是，如果您宣告屬於此型別的變數卻不使用它，並不會觸發靜態的初始設定，但如果初始設定將會變更全域狀態，這就很嚴重。  
  
 如果已內嵌初始化所有靜態資料，但未宣告明確的靜態建構函式，Microsoft Intermediate Language \(MSIL\) 編譯器就會將 `beforefieldinit` 旗標和隱含的靜態建構函式 \(它會初始化靜態資料\) 加入至 MSIL 型別定義。  當 JIT 編譯器遇到 `beforefieldinit` 旗標時，通常不會加入靜態建構函式檢查。  靜態初始設定保證會在存取任何靜態欄位之前執行，但不保證會在叫用 \(Invoke\) 靜態方法或執行個體建構函式之前執行。  請注意，靜態初始設定可以在宣告該型別的變數之後隨時進行。  
  
 靜態建構函式檢查會降低效能。  靜態建構函式通常只用於初始化靜態欄位，在這種情況下，只需確定在初次存取靜態欄位之前會執行靜態初始設定即可。  `beforefieldinit` 行為適用於這些型別與大多數其他型別。  只有當靜態初始設定會影響全域狀態，而且下列其中一項條件成立時才不適用：  
  
-   對全域狀態的影響會高度耗費資源，而且如果不使用型別，就不需要影響全域狀態。  
  
-   即使不存取型別的任何靜態欄位，也可以存取全域狀態所受到的影響。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。  
  
## 隱藏警告的時機  
 如果效能不是主要考量、透過靜態初始設定變更全域狀態需要高度耗費資源，或者必須保證會在呼叫型別的靜態方法或建立型別的執行個體之前執行全域狀態變更，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，程式碼會顯示違反規則的 `StaticConstructor` 型別，以及會以內嵌初始設定取代靜態建構函式之方式以滿足規則的 `NoStaticConstructor` 型別。  
  
 [!CODE [FxCop.Performance.RefTypeStaticCtor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor#1)]  
  
 請注意 `NoStaticConstructor` 類別 \(Class\) 之 MSIL 定義中所加入的 `beforefieldinit` 旗標。  
  
  **類別公開汽車 ansi StaticConstructor 擴充mscorlib 的類別 StaticConstructor .class 公用汽車的 ansi System.Object {} \/\/結尾 beforefieldinit NoStaticConstructor 擴充mscorlib 類別的 NoStaticConstructor System.Object {} \/\/結尾**   
## 相關規則  
 [CA2207：必須初始化實值類型的靜態欄位內嵌](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)