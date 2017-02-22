---
title: "Common Language Runtime 和運算式評估 | Microsoft Docs"
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
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估和 common language runtime"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Common Language Runtime 和運算式評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 編譯器，例如 Visual Basic 和 C\# （唸成 C sharp），以 Common Language Runtime \(CLR\) 為目標，產生 Microsoft 中繼語言 \(MSIL\)，也就是更新版本編譯的原生程式碼。 CLR 提供偵錯引擎 \(DE\) 產生的程式碼進行偵錯。 如果您打算將您專屬的程式語言整合到 Visual Studio IDE，您可以選擇要編譯為 MSIL，並因此將不需要撰寫您自己 DE。 不過，您必須撰寫能夠評估您的程式語言的內容中運算式的運算式評估工具 \(EE\)。  
  
## 討論  
 電腦語言的運算式通常會產生一組資料物件和一組用來操作這些運算子進行剖析。 例如，"A \+ B 」 可能會剖析為套用加法運算子 （\+） 資料的運算式的物件"A"和"B、"可能會導致另一個資料物件。 在程式中最常表示資料物件、 運算子和其關聯的一整組為樹狀結構，在樹狀結構節點的運算子與在分支的資料物件。 已被分成樹狀目錄格式的運算式通常稱為剖析樹狀結構。  
  
 一旦已剖析運算式，稱為來評估每個資料物件的符號提供者 \(SP\)。 例如，"A"定義在一個以上的方法，則問題"哪些 A？" A 的值都可以確定之前，必須回答。 預存程序所傳回的回應為 「 第五個堆疊框架上第三個項目 」 或者 「 超過靜態記憶體的開頭的 50 個位元組的配置給此方法 」。  
  
 除了程式本身的產生 MSIL，CLR 編譯器也會產生程式資料庫 \(.pdb\) 檔案中會寫入偵錯相當的描述性資訊。 專屬語言編譯器會產生相同的格式為 CLR 編譯器的偵錯資訊，因為 CLR 預存程序就能識別語言的具名資料物件。 具名的資料物件識別之後, EE 會使用繫結器物件產生關聯 （或繫結） 資料物件會保留該物件的值之記憶體區域。 DE 可以取得或設定新的資料物件的值。  
  
 專利的編譯器可以提供 CLR 偵錯資訊，藉由呼叫 `ISymbolWriter` 介面 \(定義於.NET Framework 命名空間中 `System.Diagnostics.SymbolStore`\)。 專利的編譯器編譯為 MSIL，並寫入偵錯資訊，透過這些介面，可以使用 CLR DE 和 SP 這可大幅簡化將專屬的語言整合到 Visual Studio IDE。  
  
 當 CLR DE 呼叫專屬的 EE 評估運算式時，DE 提供 EE 包含預存程序並繫結器物件的介面。 因此，撰寫 CLR 為基礎的偵錯引擎方法就必須只實作適當的運算式評估工具的介面。CLR 會負責繫結，以及為您處理的符號。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)