---
title: "堆疊框架 | Microsoft Docs"
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
  - "堆疊框架，偵錯"
  - "偵錯 [偵錯 SDK]，堆疊框架"
  - "堆疊框架"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 堆疊框架
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯工具的架構的角度來看**的堆疊框架**：  
  
-   是提供執行緒的執行內容堆疊的抽象概念。  執行緒永遠是函式中執行。  堆疊框架會保留其區域變數的函式和引數。  若要使用 Visual Studio 進行偵錯時，其語言或正在進行偵錯的環境必須支援堆疊框架。  
  
-   可以同時識別並描述它自己，並可傳回關聯性的執行緒。  程式碼內容，表示目前的指令指標，以及相關的文件和運算式評估內容，也可以傳回堆疊框架。  
  
-   具有的屬性的描述名稱、 類型和區域變數、 引數的值，並出現各種不同的 IDE 偵錯視窗中。  
  
-   由[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，通常由偵錯引擎 \(DE\) 或虛擬機器執行執行緒的建立。  
  
## 請參閱  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)