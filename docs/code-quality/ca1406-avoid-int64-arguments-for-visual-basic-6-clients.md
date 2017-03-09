---
title: "CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數 | Microsoft Docs"
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
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 特別標記為元件物件模型 \(COM\) 可見的型別，會宣告採用 <xref:System.Int64?displayProperty=fullName> 引數的成員。  
  
## 規則描述  
 Visual Basic 6 COM 用戶端無法存取 64 位元整數。  
  
 根據預設，COM 可以看見下列各項：組件、公用型別、公用型別中的公用執行個體 \(Instance\) 成員，和公用實值型別的所有成員。  但是，為了減少誤報的情形，這項規則要求必須明確陳述此型別的 COM 可視性、必須使用設定為 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 來標記包含的組件，而且必須使用設定為 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 來標記此型別。  
  
## 如何修正違規  
 若要針對參數修正這個規則的違規情形，而這個參數的值一律是以 32 位元整數類表示，請將參數型別變更成 <xref:System.Int32?displayProperty=fullName>。  如果參數的值可能大於可用 32 位元整數類表示的值，請將參數型別變更成 <xref:System.Decimal?displayProperty=fullName>。  請注意，<xref:System.Single?displayProperty=fullName> 及 <xref:System.Double?displayProperty=fullName> 在 <xref:System.Int64> 資料型別的範圍上限都會遺失精確度。  如果不需要在 COM 中看到成員，請利用已設定為 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 來標記它。  
  
## 隱藏警告的時機  
 如果確定 Visual Basic 6 COM 用戶端不會存取該型別，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例顯示違反規則的型別。  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## 相關規則  
 [CA1413：避免在 COM 可見的實值類型中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可見類型中使用靜態成員](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：以 ComVisibleAttribute 標記組件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)