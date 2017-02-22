---
title: "CA2201：不要引發保留的例外狀況類型 | Microsoft Docs"
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
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201：不要引發保留的例外狀況類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## 原因  
 方法所引發的例外狀況型別過於一般性，或是執行階段所保留的型別。  
  
## 規則描述  
 下列的例外狀況型別過於一般性，無法提供使用者足夠的資訊：  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 下列的例外狀況型別已保留，只能由 Common Language Runtime 擲回：  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **請勿擲回一般例外狀況**  
  
 如果擲回一般例外狀況型別，例如程式庫或架構中的 <xref:System.Exception> 或 <xref:System.SystemException>，會強制消費者攔截所有例外狀況，包括他們不知該如何處理的未知例外狀況。  
  
 請改為擲回在架構中已經存在的更為衍生的型別，或是您自己建立衍生自 <xref:System.Exception> 的型別。  
  
 **擲回特定例外狀況**  
  
 下表顯示參數以及驗證該參數時所擲回的例外狀況 \(包括屬性 set 存取子中的值參數\)：  
  
|參數描述|例外狀況|  
|----------|----------|  
|`null` 參考|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|超過允許值範圍 \(例如集合或清單的索引\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|無效 `enum` 值|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|包含的格式不符合方法的參數規格 \(例如 `ToString(String)` 的格式字串\)|<xref:System.FormatException?displayProperty=fullName>|  
|因其他原因失效|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 當作業對物件目前狀態無效時，擲回 <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 當作業在已經處置的物件上執行時，擲回 <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 當不支援作業 \(例如在為讀取而開啟的資料流中覆寫 **Stream.Write**\) 時，擲回 <xref:System.NotSupportedException?displayProperty=fullName>  
  
 當轉換會造成溢位 \(例如明確轉型運算子多載\) 時，擲回 <xref:System.OverflowException?displayProperty=fullName>  
  
 至於所有其他的情況，請考慮您自己建立衍生自 <xref:System.Exception> 的型別以擲回。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將擲回的例外狀況型別變更為保留型別以外的特定型別。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 相關規則  
 [CA1031：不要攔截一般例外狀況類型](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)