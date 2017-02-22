---
title: "CA1021：避免使用 out 參數 | Microsoft Docs"
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
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1021：避免使用 out 參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|AvoidOutParameters|  
|CheckId|CA1021|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用型別中之公用或保護的方法具有 `out` 參數。  
  
## 規則描述  
 以傳址方式傳遞型別時 \(使用 `out` 或 `ref`\)，您需要擁有使用指標的經驗、了解實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。  不過 `out` 和 `ref` 參數之間的差異一般人不甚了解。  
  
 以「傳址方式」傳遞參考型別時，方法會使用參數傳回不同的物件執行個體   以傳址方式傳遞參考型別也就是使用雙重指標、指標對指標或雙重間接取值 \(Indirection\)。  藉由使用以「傳值方式」傳遞的預設呼叫慣例 \(Calling Convention\)，採用參考型別的參數即已經接收到物件的指標。  以傳值方式傳遞指標，而不是傳遞所指向的物件。  以傳值方式傳遞代表方法不能變更指標，讓指標指向參考型別的新執行個體。  但是，它可以變更所指向物件的內容。  對大多數應用程式來說，這樣就已足夠並可產生想要的行為。  
  
 如果方法必須傳回不同的執行個體，請使用方法的傳回值以完成這項作業。  請參閱 <xref:System.String?displayProperty=fullName> 類別，以取得在字串上作業並傳回字串新執行個體的多種方法。  使用這個模型時，呼叫端必須決定是否要保留原始物件。  
  
 雖然傳回值很常見並且大量使用，但還是需要中等的設計和編碼技能，才能正確地應用 `out` 和 `ref` 參數。  針對一般使用者所設計的程式庫架構不應預期使用者會熟練地運用 `out` 或 `ref` 參數。  
  
## 如何修正違規  
 若要修正因實值型別而引發此規則的違規情形，可讓方法傳回物件當做它的傳回值。  如果方法必須傳回多個值，請將方法重新設計，以傳回持有值之物件的單一執行個體。  
  
 若要修正因參考型別而引發此規則的違規情形，請確定所需的行為就是傳回參考的新執行個體。  如果是，則方法應使用它的傳回值以完成這項作業。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。  然而，這種設計可能會造成可用性問題。  
  
## 範例  
 下列程式庫會示範類別的兩種實作，而這個類別會產生使用者意見的回應。  第一個實作 \(`BadRefAndOut`\) 會強制程式庫使用者管理三個傳回值。  而第二個實作 \(`RedesignedRefAndOut`\) 會透過傳回容器 \(Container\) 類別 \(`ReplyData`\) 的執行個體，將資料當成單一單位管理，進而簡化使用者的經驗。  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## 範例  
 下列應用程式會說明使用者經驗。  對重新設計之程式庫 \(`UseTheSimplifiedClass` 方法\) 的呼叫將會更明確易懂，因此能夠更容易地管理方法所傳回的資訊。  而這兩個方法的輸出都一樣。  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## 範例  
 下列範例程式庫將說明如何使用參考型別的 `ref` 參數，並顯示實作這項功能的較佳方法。  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## 範例  
 下列應用程式會在程式庫中呼叫每個方法，以示範行為。  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 這個範例產生下列輸出。  
  
  **變更指標 \- 以傳值方式傳遞：**  
**12345**  
**12345**  
**變更指標 \- 以傳址方式傳遞：**  
**12345**  
**12345 ABCDE**  
**透過傳回值傳遞：**  
**12345 ABCDE**   
## Try 模式方法  
  
### 說明  
 實作 **Try\<Something\> 模式的方法 \(例如** <xref:System.Int32.TryParse%2A?displayProperty=fullName>\) 不會引發這個違規。  下列範例顯示實作 <xref:System.Int32.TryParse%2A?displayProperty=fullName> 方法的結構 \(實值型別，Value Type\)。  
  
### 程式碼  
 [!CODE [FxCop.Design.TryPattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern#1)]  
  
## 相關規則  
 [CA1045：不要以傳址方式傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)