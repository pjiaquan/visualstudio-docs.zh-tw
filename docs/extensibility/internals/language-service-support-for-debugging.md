---
title: "語言服務支援偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯工具、 語言支援"
  - "偵錯支援的語言服務"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 語言服務支援偵錯
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

語言服務可以提供功能，可支援偵錯工具透過 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> 介面。 這些功能包括驗證中斷點，並提供一份運算式 **自動變數** 視窗。  
  
 不過，您需要有偵錯您的語言的運算式評估工具。 運算式評估工具會負責評估運算式以產生偵錯時的值。 如需實作 CLR 運算式評估工具的資訊，請參閱:  
  
-   [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Managed 的運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## 編譯器輸出  
 編譯器的類型會決定您要如何實作偵錯您的語言。 如果您的編譯器 Windows 作業系統為目標，並將寫入.pdb 檔案，您可以使用原生程式碼偵錯引擎整合至 Visual Studio 偵錯程式。 如果您的編譯器會產生 Microsoft 中繼語言 \(MSIL\)，您可以使用 managed 程式碼偵錯引擎，也會整合至 Visual Studio 偵錯程式。 如果您的編譯器目標是專用的作業系統或不同的執行階段環境，您需要撰寫您自己的偵錯引擎。  
  
 如需有關如何實作您的語言偵錯的詳細資訊，請參閱 [使用者入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Visual Studio 偵錯 SDK 中。