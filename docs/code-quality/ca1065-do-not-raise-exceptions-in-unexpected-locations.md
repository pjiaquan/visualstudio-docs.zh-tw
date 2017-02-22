---
title: "CA1065：不要在非預期的位置中引發例外狀況 | Microsoft Docs"
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
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1065：不要在非預期的位置中引發例外狀況
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|分類|Microsoft.Design|  
|中斷變更|不中斷|  
  
## 原因  
 不可擲回例外狀況 \(Exception\) 的方法卻擲回例外狀況。  
  
## 規則描述  
 不可擲回例外狀況的方法可以分成下列幾類：  
  
-   Property Get 方法  
  
-   事件存取子方法  
  
-   Equals 方法  
  
-   GetHashCode 方法  
  
-   ToString 方法  
  
-   靜態建構函式 \(Constructor\)  
  
-   完成項  
  
-   Dispose 方法  
  
-   等號比較運算子  
  
-   隱含轉型運算子  
  
 下列章節會討論這些方法類型。  
  
### Property Get 方法  
 屬性基本上是智慧型欄位。  因此，應該讓屬性的行為盡量類似欄位。  欄位不會擲回例外狀況，所以屬性也不能擲回例外狀況。  如果某個屬性會擲回例外狀況，請考慮將它變成方法。  
  
 可以從 Property Get 方法擲回的例外狀況包括：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> 和所有系出物件 \(包括 <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> 和所有系出物件  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(只能從索引 Get 擲回\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(只能從索引 Get 擲回\)  
  
### 事件存取子方法  
 事件存取子應該是不允許擲回例外狀況的簡單作業。  事件不可在嘗試加入或移除事件處理常式時擲回例外狀況。  
  
 可從事件存取子擲回的例外狀況包括：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> 和所有系出物件 \(包括 <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> 和所有系出物件  
  
-   <xref:System.ArgumentException> 和系出物件  
  
### Equals 方法  
 下列 **Equals** 方法不可擲回例外狀況：  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M: IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Equals** 方法應該傳回 `true` 或 `false`，而不是擲回例外狀況。  例如，如果將兩個不相符的型別傳遞到 Equals，它應該只會傳回 `false`，而不會擲回 <xref:System.ArgumentException>。  
  
### GetHashCode 方法  
 下列 **GetHashCode** 方法通常不可擲回例外狀況：  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M: IEqualityComparer.GetHashCode \(Of T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** 必須傳回值，  否則，您可能會遺失雜湊資料表中的項目。  
  
 可接受引數的 **GetHashCode** 版本可以擲回 <xref:System.ArgumentException>。  不過，**Object.GetHashCode** 絕對不可擲回例外狀況。  
  
### ToString 方法  
 偵錯工具使用 <xref:System.Object.ToString%2A?displayProperty=fullName>，以字串格式顯示物件相關資訊。  因此，**ToString** 不應該變更物件的狀態，也不可擲回例外狀況。  
  
### 靜態建構函式 \(Constructor\)  
 從靜態建構函式傳回例外狀況，將使型別無法在目前的應用程式定義域中使用。  除非有非常充分的理由 \(例如安全性問題\)，否則請勿從靜態建構函式擲回例外狀況。  
  
### 完成項  
 從完成項擲回例外狀況將使 CLR 執行失敗，而導致處理序終止。  因此，請務必避免在完成項中擲回例外狀況。  
  
### Dispose 方法  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 方法不應擲回例外狀況。  Dispose 通常是在 `finally` 子句的清除邏輯中一併呼叫。  因此，從 Dispose 明確擲回例外狀況將會強制使用者在 `finally` 子句中加入例外處理 \(Exception Handling\)。  
  
 **Dispose\(false\)** 程式碼路徑絕對不可擲回例外狀況，因為這個路徑幾乎都是從完成項呼叫。  
  
### 等號比較運算子 \(\=\=、\!\=\)  
 就像 Equals 方法一樣，等號比較運算子應該傳回 `true` 或 `false`，而不可擲回例外狀況。  
  
### 隱含轉型運算子  
 因為使用者通常不會察覺到已經呼叫了隱含轉型運算子，所以完全不會預期到隱含轉型運算子擲回的例外狀況。  因此，您不可從隱含轉型運算子擲回任何例外狀況。  
  
## 如何修正違規  
 對於屬性 getter，請變更邏輯使它不再需要擲回例外狀況，或是將屬性變更為方法。  
  
 對於先前列出的所有其他方法型別，請變更邏輯使它不再需要擲回例外狀況。  
  
## 隱藏警告的時機  
 如果違規是因例外狀況宣告而非擲回例外狀況所造成，則您可以放心地隱藏這項規則的警告。  
  
## 相關規則  
 [CA2219：不要在 exception 子句中引發例外狀況](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)  
  
## 請參閱  
 [設計警告](../code-quality/design-warnings.md)