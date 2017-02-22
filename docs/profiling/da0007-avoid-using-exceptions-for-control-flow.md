---
title: "DA0007：避免使用例外狀況進行控制流程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0007：避免使用例外狀況進行控制流程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0007|  
|分類|.NET Framework 使用|  
|程式碼剖析方法|全部|  
|Message|持續有大量例外狀況擲回。  請考慮在程式邏輯中減少例外狀況的使用。|  
|訊息類型|警告|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 25 個範本才能觸發此規則。  
  
## 原因  
 程式碼剖析資料中呼叫了高比率的 .NET Framework 例外狀況處理常式。  請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數目。  
  
## 規則描述  
 雖然使用例外狀況處理常式來攔截錯誤和會中斷程式執行的其他事件是良好的作法，使用例外狀況處理常式做為規則程式執行邏輯的部分，可能會耗費許多資源，而且應該盡量避免。  在大多數情況下，都應該只針對很少發生和非預期的情況使用例外狀況。  例外狀況不應在一般程式流程時用來傳回值。  在許多情況下，您可以藉由驗證值和使用條件式邏輯來暫止會造成問題之陳述式的執行，以避免引發例外狀況。  
  
 如需詳細資訊請參閱在 MSDN 程式庫區段中， **Microsoft Patterns and Practices Improving .NET Application Performance and Scalability Chapter 5 — Improving Managed Code Performance**[例外狀況管理](http://go.microsoft.com/fwlink/?LinkID=177825)。  
  
## 如何調查警告  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至標記檢視。  尋找包含 \[**.NET CLR Exceptions\(@ProcessInstance\)\\\# of Exceps Thrown \/ sec**\] 度量的資料行。  判斷是否有特定的程式執行階段，其中例外狀況處理比其他階段更為頻繁。  使用取樣設定檔，嘗試識別經常產生例外狀況的 throw 陳述式和 try\/catch 區塊。  必要時，將邏輯加入至 catch 區塊，以協助您了解哪些例外狀況最常被處理。  請盡可能以簡單的流程控制邏輯或驗證程式碼，來取代經常執行的 throw 陳述式或 catch 區塊。  
  
 例如，如果您發現自己的應用程式有處理頻繁的 DivideByZeroException 例外狀況，將邏輯加入程式以檢查具有零值的分母，就會改善應用程式的效能。