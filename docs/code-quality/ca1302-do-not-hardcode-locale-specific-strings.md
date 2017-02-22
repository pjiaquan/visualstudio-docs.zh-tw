---
title: "CA1302：請勿於程式中定義地區設定專屬的字串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1302：請勿於程式中定義地區設定專屬的字串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 方法會使用字串常值 \(String Literal\)，表示某些系統資料夾的路徑部分。  
  
## 規則描述  
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> 列舉型別 \(Enumeration\) 包含參考特殊系統資料夾的成員。  這些資料夾的位置在不同的作業系統上可有不同的值，使用者可以變更某些位置，而且位置會當地語系化。  特殊資料夾的一個範例是系統資料夾。在 [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] 是 "C:\\WINDOWS\\system32"，但在 [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] 上則是 "C:\\WINNT\\system32"。  <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> 方法會傳回與 <xref:System.Environment.SpecialFolder> 列舉相關聯的位置。  由 <xref:System.Environment.GetFolderPath%2A> 所傳回的位置會當地語系化，並且適用於目前執行中的電腦。  
  
 這項規則會將使用 <xref:System.Environment.GetFolderPath%2A> 方法所擷取的資料夾路徑，語彙基元化到不同的目錄層級。  每個字串常值會與語彙基元比較。  如果找到相符項目，則假設方法正在建置的字串會參考與此語彙基元關聯的系統位置。  針對可攜性和可當地語系化，請使用 <xref:System.Environment.GetFolderPath%2A> 方法而非字串常值，擷取特殊系統資料夾的位置。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用 <xref:System.Environment.GetFolderPath%2A> 方法擷取位置。  
  
## 隱藏警告的時機  
 如果字串常值並未用於參考與 <xref:System.Environment.SpecialFolder> 列舉關聯的其中一個系統位置，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會建置通用應用程式儲存資料夾的路徑，此資料夾會根據此規則產生三個警告。  此範例接著會使用 <xref:System.Environment.GetFolderPath%2A> 方法擷取路徑。  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## 相關規則  
 [CA1303：不要將常值當做已當地語系化的參數傳遞](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)