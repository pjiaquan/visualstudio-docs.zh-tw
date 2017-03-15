---
title: "使用 Assert 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert 類別"
  - "Assert 陳述式"
  - "單元測試，Assert 陳述式"
  - "單元測試，Assert 類別"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# 使用 Assert 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

請使用 UnitTestingFramework 命名空間的 Assert 類別，以驗證特定功能。  單元測試方法會執行開發程式碼中方法的程式碼，但是只有在加入 Assert 陳述式時，才會產生程式碼的行為方面正確性的報告。  
  
## Assert 的種類  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間提供數種 Assert 類別：  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 在測試方法中，您可以呼叫任何數目的 Assert 類別方法，例如 Assert.AreEqual\(\)。  Assert 類別具有許多可用的方法，而那其中有許多方法具有數個多載。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 請使用 CollectionAssert 類別比較物件的集合，並驗證一或多個集合的狀態。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 請使用 StringAssert 類別比較字串。  這個類別包含各種有用的方法，例如 StringAssert.Contains、StringAssert.Matches 和 StringAssert.StartsWith。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 每當測試失敗時，都會擲回 AssertFailedException 例外狀況。  如果測試逾時、擲回未預期的例外狀況，或有 Assert 陳述式產生失敗的結果，則測試失敗。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 每當測試產生結果不明的結果時，就會擲回 AssertInconclusiveException。  一般而言，建議將 Assert.Inconclusive 陳述式加入至仍在處理的測試，以指示測試未準備好執行。  
  
> [!NOTE]
>  另一個方法就是，利用 Ignore 屬性 \(Attribute\) 標示未準備好執行的測試。  不過，這個方法有個缺點，就是您無法根據尚未實作的測試數目輕易地產生報告。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 如果您撰寫新的 Assert 例外狀況類別，那麼讓該類別繼承自基底類別 UnitTestAssertException，便可以更輕鬆地將例外狀況識別為判斷提示 \(Assertion\) 失敗，而非測試或實際執行程式碼所擲回的未預期例外狀況。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 當您希望測試方法驗證預期由開發程式碼之方法擲回的例外狀況，確實是由該方法擲回，請使用 ExpectedExceptionAttribute 屬性裝飾測試方法。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/zh-tw/e8370b93-085b-41c9-8dec-655bd886f173)