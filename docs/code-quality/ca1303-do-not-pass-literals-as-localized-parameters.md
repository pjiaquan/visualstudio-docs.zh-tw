---
title: "CA1303：不要將常值當做已當地語系化的參數傳遞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303：不要將常值當做已當地語系化的參數傳遞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|分類|Microsoft.Globalization|  
|中斷變更|不中斷|  
  
## 原因  
 方法將字串常值當做參數傳遞至 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 中的建構函式或方法，且該字串應該可以當地語系化。  
  
 將常值字串做為值傳遞至參數或屬性，而且下列一或多列個況為真時，就會引發這個警告：  
  
-   參數或屬性 \(property\) 的 <xref:System.ComponentModel.LocalizableAttribute> 屬性 \(attribute\) 設定為 true。  
  
-   參數或屬性名稱包含「文字」、「訊息」或「標題」。  
  
-   傳遞至 Console.Write 或 Console.WriteLine 方法之字串參數的名稱為 "value" 或 "format"。  
  
## 規則描述  
 內嵌在原始程式碼中的字串常值難以當地語系化。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請以透過 <xref:System.Resources.ResourceManager> 類別的執行個體 \(Instance\) 擷取的字串取代字串常值。  
  
## 隱藏警告的時機  
 如果不會將程式碼程式庫當地語系化，或者不會使用程式碼程式庫將字串公開 \(Expose\) 給使用者或程式開發人員，則您可以放心地隱藏這項規則的警告。  
  
 使用者可以消除這些不應該透過更改具名之參數或屬性的名稱，或將這些項目當做條件式的方式，來傳遞已當地語系化字串的方法所造成的干擾。  
  
## 範例  
 下列範例會顯示當方法的兩個引數的其中一個超出範圍時，擲回例外狀況的方法。  針對第一個引數，例外狀況建構函式會傳遞常值字串，因此會違反此規則。  針對第二個引數，建構函式會正確地傳遞透過 <xref:System.Resources.ResourceManager> 擷取的字串。  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## 請參閱  
 [桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)