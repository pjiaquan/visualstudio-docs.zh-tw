---
title: "撰寫通用語言執行階段運算式評估工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估工具、 教學課程"
  - "運算式評估、 範例"
  - "偵錯 [偵錯 SDK]，運算式評估工具教學課程"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 撰寫通用語言執行階段運算式評估工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 偵錯引擎 \(DE\) 處理之語法的一部分而產生的程式碼進行偵錯的程式語言的語意 \(semantics\) 運算式評估工具 \(EE\)。 運算式必須評估內容中的程式語言。 例如，在某些語言中，"A \+ B"的運算式表示 「 的總和與 B 」 在其他語言中，相同的運算式可能是指"A 或 B 」。 因此，個別 EE 必須撰寫為每個 Visual Studio IDE 中產生物件来進行偵錯的程式碼的程式設計語言。  
  
 Visual Studio 偵錯封裝的某些層面必須解譯程式語言的內容中的程式碼。 比方說，當執行暫止於中斷點時，任何使用者已輸入的運算式 **監看式** 必須評估並顯示視窗。 此外，使用者可以變更本機變數的值輸入到運算式 **監看式** 視窗或 **即時運算** 視窗。  
  
## 在本節中  
 [Common Language Runtime 和運算式評估](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 說明，當您要將專屬的程式語言整合到 Visual Studio IDE 中，撰寫 EE 能夠評估運算式內容中的專用語言可讓您不需要撰寫偵錯引擎會編譯成 Microsoft 中繼語言 \(MSIL\)。  
  
 [運算式評估工具架構](../../extensibility/debugger/expression-evaluator-architecture.md)  
 討論如何實作必要的 EE 介面和呼叫的通用語言執行階段符號提供者 \(SP\) 和繫結器介面。  
  
 [註冊的運算式評估工具](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 附註 EE 必須註冊本身作為類別處理站與通用語言執行平台和 Visual Studio 執行階段環境。  
  
 [實作運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 描述如何評估運算式的程序包括偵錯引擎 \(DE\)、 符號提供者 \(SP\)、 繫結器物件，以及運算式評估工具 \(EE\)。  
  
 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md)  
 描述如何，當執行暫停時，偵錯封裝呼叫 DE 來取得本機變數和引數的清單。  
  
 [監看式\] 視窗中的運算式評估](../Topic/Evaluating%20a%20Watch%20Window%20Expression.md)  
 說明 Visual Studio 偵錯封裝如何呼叫 DE，以判斷其監看清單中的每個運算式的目前值。  
  
 [變更本機值](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 說明在本機的值變更，\[區域變數\] 視窗的每一行有相關聯的物件，提供名稱、 類型和區域的目前值。  
  
 [實作類型的視覺化檢視和自訂檢視器](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 說明哪些介面必須由哪一個元件，以支援類型的視覺化檢視和自訂檢視器來實作。  
  
## 請參閱  
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)