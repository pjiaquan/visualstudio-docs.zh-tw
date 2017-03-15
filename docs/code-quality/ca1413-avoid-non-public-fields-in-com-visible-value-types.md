---
title: "CA1413：避免在 COM 可見的實值類型中使用非公用欄位 | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413：避免在 COM 可見的實值類型中使用非公用欄位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 特別標示為元件物件模型 \(COM\) 可見的實值型別宣告了非公用執行個體欄位。  
  
## 規則描述  
 COM 可見實值型別的非公用執行個體欄位對 COM 用戶端而言是可見的。  請檢閱不應該公開之資訊的欄位內容，或是會造成未預期的設計或安全性結果的欄位內容。  
  
 依照預設，所有公用的實值型別對 COM 而言都是可見的。  但是，為了減少誤報，此規則要求必須明確指定型別的 COM 可視性。  包含的組件必須以設定為 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 來標示，而型別必須以設定為 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 來標示。  
  
## 如何修正違規  
 若要修正此規則的違規情形並繼續隱藏欄位，請將實值型別變更為參考型別 \(Reference Type\)，或從型別中移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性 \(Attribute\)。  
  
## 隱藏警告的時機  
 如果公開此欄位是可接受的，則您可以放心地隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反規則的型別。  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## 相關規則  
 [CA1407：避免在 COM 可見類型中使用靜態成員](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：以 ComVisibleAttribute 標記組件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [限定互通的 .NET 類型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)