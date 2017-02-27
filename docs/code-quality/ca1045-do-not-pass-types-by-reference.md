---
title: "CA1045：不要以傳址方式傳遞類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1045：不要以傳址方式傳遞類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用 \(Public\) 型別中之公用或保護的方法具有 `ref` 參數，此參數會採用基本型別 \(Primitive Type\)、參考型別 \(Reference Type\)，或者是不屬於任一內建型別的實值型別 \(Value Type\)。  
  
## 規則描述  
 以傳址方式傳遞型別時 \(使用 `out` 或 `ref`\)，您需要擁有使用指標的經驗、了解實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。  不過 `out` 和 `ref` 參數之間的差異一般人不甚了解。  
  
 以「傳址方式」傳遞參考型別時，方法會使用參數傳回不同的物件執行個體 \(以傳址方式傳遞參考型別也就是使用雙重指標、指標對指標或雙重間接取值 \(Indirection\)\)。使用預設呼叫慣例 \(Calling Convention\) 時 \(以「傳值方式」傳遞\)，採用參考型別的參數已接收到物件的指標。  以傳值方式傳遞指標，而不是傳遞所指向的物件。  以傳值方式傳遞表示方法無法將指標變更為指向參考型別的新執行個體，但是可變更所指向的物件內容。  對於大多數的應用程式而言，這就足夠而且會產生您想要的行為。  
  
 如果方法必須傳回不同的執行個體，請使用方法的傳回值以完成這項作業。  請參閱 <xref:System.String?displayProperty=fullName> 類別，以取得在字串上作業並傳回字串新執行個體的多種方法。  使用此模型可讓呼叫端決定是否要保留原始物件。  
  
 雖然傳回值很常見並且大量使用，但還是需要中等的設計和編碼技能，才能正確地應用 `out` 和 `ref` 參數。  針對一般使用者所設計的程式庫架構不應預期使用者會熟練地運用 `out` 或 `ref` 參數。  
  
> [!NOTE]
>  當您使用大型結構的參數時，複製這些結構所需的其他資源，可能會在以傳值方式傳遞時影響效能。  在這些情況下，您可以考慮使用 `ref` 或 `out` 參數。  
  
## 如何修正違規  
 若要修正因實值型別而引發此規則的違規情形，可讓方法傳回物件當做它的傳回值。  如果方法必須傳回多個值，請將方法重新設計，以傳回持有值之物件的單一執行個體。  
  
 若要修正參考型別所造成的違規情形，請確定您想要的行為就是傳回參考的新執行個體。  如果是，則方法應使用它的傳回值以完成這項作業。  
  
## 隱藏警告的時機  
 您可以放心地隱藏這項規則的警告。不過，這種設計可能會造成可用性的問題。  
  
## 範例  
 下列程式庫會示範類別的兩種實作，而這個類別會產生使用者意見的回應。  第一個實作 \(`BadRefAndOut`\) 會強制程式庫使用者管理三個傳回值。  而第二個實作 \(`RedesignedRefAndOut`\) 會透過傳回容器 \(Container\) 類別 \(`ReplyData`\) 的執行個體，將資料當成單一單位管理，進而簡化使用者的經驗。  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## 範例  
 下列應用程式會說明使用者經驗。  對重新設計之程式庫 \(`UseTheSimplifiedClass` 方法\) 的呼叫將會更明確易懂，因此能夠更容易地管理方法所傳回的資訊。  而這兩個方法的輸出都一樣。  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## 範例  
 下列範例程式庫將說明如何使用參考型別的 `ref` 參數，並顯示實作這項功能的較佳方法。  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## 範例  
 下列應用程式會在程式庫中呼叫每個方法，以示範行為。  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 這個範例產生下列輸出。  
  
  **變更指標 \- 以傳值方式傳遞：**  
**12345**  
**12345**  
**變更指標 \- 以傳址方式傳遞：**  
**12345**  
**12345 ABCDE**  
**透過傳回值傳遞：**  
**12345 ABCDE**   
## 相關規則  
 [CA1021：避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)