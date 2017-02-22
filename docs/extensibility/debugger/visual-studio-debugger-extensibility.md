---
title: "Visual Studio 偵錯工具擴充性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [Visual Studio]、 [偵錯 sdk 》"
  - "偵錯 SDK"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio 偵錯工具擴充性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 包含具全面互動性的來源的程式碼偵錯工具，提供功能強大且容易使用的工具來追蹤您的程式中的錯誤。 偵錯工具有完整的支援 Visual Basic、 C\#、 C\/c \+ \+ 和 JavaScript。 不過，若使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], ，也就是可從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkId=214453),, 、 其他程式設計語言可支援在相同的豐富功能的偵錯工具。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具是常見的前端 （也就是使用者介面），因此，偵錯的語言專屬的偵錯元件。 新的語言所需的所有支援 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具會建立必要的後端元件，例如偵錯引擎 \(DE\)。 這時 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 進來。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 包含所有的完整參考 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建立新的 DE 所需的項目。 此外，還有範例和教學課程，可幫助您入門。  
  
 如需偵錯支援的語言專案系統的端對端範例，請參閱 [IronPython sample](http://msdn.microsoft.com/zh-tw/4c41695c-12c1-4670-b43b-d8d84c9e4089)。  
  
 下列各節說明如何使用偵錯工具來擴充 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
## 在本節中  
 [使用者入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 說明何謂 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 優惠，以及如何安裝 SDK 時，偵錯。  
  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 文件的自訂 DE 程序，來卸離 DE DE 準備您的程式。  
  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 說明您的電腦必須撰寫的運算式評估工具。  
  
 [選擇偵錯引擎的實作策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 討論如何實作您 DE。  
  
 [參考資料](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 文件 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯 API。  
  
 [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 包含通用語言執行階段運算式評估工具範例和偵錯引擎範例連結。