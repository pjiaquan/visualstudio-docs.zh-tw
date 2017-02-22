---
title: "CA1305：指定 IFormatProvider | Microsoft Docs"
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
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1305：指定 IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 方法或建構函式 \(Constructor\) 所呼叫的一或多個成員具有可接受 <xref:System.IFormatProvider?displayProperty=fullName> 參數的多載，但該方法或建構函式並未呼叫可接受 <xref:System.IFormatProvider> 參數的多載。  此規則會忽略對 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 方法的呼叫，這些方法已記錄為忽略 <xref:System.IFormatProvider> 參數，以及下列方法：  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## 規則描述  
 如果未提供 <xref:System.Globalization.CultureInfo?displayProperty=fullName> 或 <xref:System.IFormatProvider> 物件，則多載成員所提供的預設值並非在所有地區設定中都會產生您想要的作用。  此外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 成員可能會選擇預設的文化特性 \(Culture\) 和格式，但是它所根據的假設對您的程式碼而言可能是錯誤的。  若要確保程式碼能如預期般在案例中運作，您必須根據下列方針提供文化特性資訊：  
  
-   如果要對使用者顯示值，請使用目前的文化特性。  請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。  
  
-   如果要讓軟體儲存或存取值 \(在檔案或資料庫內保存\)，請使用不因文化特性而異的值。  請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  
  
-   如果您不知道值的目的端，請讓資料消費者 \(Data Consumer\) 或提供者指定文化特性。  
  
 請注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 只用於使用 <xref:System.Resources.ResourceManager?displayProperty=fullName> 類別 \(Class\) 的執行個體擷取當地語系化資源。  
  
 即使多載成員的預設行為不符合需要，您最好能明確呼叫文化特性的多載，讓程式碼可以自我記錄，也會更容易維護。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用接受 <xref:System.Globalization.CultureInfo> 或 <xref:System.IFormatProvider> 的多載，並根據先前列出的方針指定引數。  
  
## 隱藏警告的時機  
 當您確定預設的文化特性\/格式提供者是正確的選擇，而且程式碼維護性不是重要的優先開發考量，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 在下列範例中，`BadMethod` 會造成這條規則的兩個違規。  `GoodMethod` 藉由將不因國別而異的文化特性傳遞至 <xref:System.String.Compare%2A>，修正第一個違規，並藉由將目前的文化特性傳遞至 <xref:System.String.ToLower%2A>，修正第二個違規，這是因為已經向使用者顯示 `string3`。  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## 範例  
 在下列範例中，程式碼會顯示目前的文化特性對 <xref:System.DateTime> 型別選取之預設 <xref:System.IFormatProvider> 的效果。  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 這個範例產生下列輸出。  
  
  **6\/15\/2009 1:45:30 PM \-\> 2009\-06\-15T13:45:30.0900000**   
## 相關規則  
 [CA1304：指定 CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## 請參閱  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/zh-tw/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)