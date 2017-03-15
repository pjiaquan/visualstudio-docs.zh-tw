---
title: "CA1306：設定資料類型的地區設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1306：設定資料類型的地區設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 方法或建構函式 \(Constructor\) 建立了一或多個 <xref:System.Data.DataTable?displayProperty=fullName> 或 <xref:System.Data.DataSet?displayProperty=fullName> 執行個體，而且並未明確設定地區設定 \(Locale\) 屬性 \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> 或 <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\)。  
  
## 規則描述  
 地區設定會決定資料的文化特性特定展示項目，例如用於數值、貨幣符號和排序次序的格式。  當您建立 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 時，您應該明確設定地區設定。  根據預設，這些型別的地區設定為目前的文化特性。  對於儲存在資料庫或檔案中而且全域共用的資料而言，地區設定通常必須設定為不因文化特性而異 \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\)。  當資料共用於文化特性之間時，使用預設地區設定會造成 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容展示或解譯不正確。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請明確設定 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的地區設定。  
  
## 隱藏警告的時機  
 當程式庫或應用程式適用於有限制的地區設定使用者、資料並未共用，或預設值可在所有支援的情節中產生想要的行為時，您就可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會建立兩個 <xref:System.Data.DataTable> 執行個體。  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## 請參閱  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>