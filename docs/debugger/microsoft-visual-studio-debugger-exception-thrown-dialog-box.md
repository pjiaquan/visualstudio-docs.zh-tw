---
title: "Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊"
  - "例外狀況處理, 偵錯期間"
  - "偵錯工具, 例外狀況"
  - "擲回例外狀況, 偵錯期間"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您的程式發生了例外狀況。  這個對話方塊將報告擲回的例外狀況類型。  您的程式碼需要處理這個例外狀況。  您可以選擇下列選項處理例外狀況：  
  
 **Break**  
 允許執行中斷偵錯工具。  中斷之前沒有叫用例外狀況處理常式。  如果您從中斷處繼續，就會叫用例外狀況處理常式。  
  
 **繼續**  
 允許繼續執行，讓例外狀況處理常式有機會處理例外狀況。  這個選項不適用於某些例外狀況類型。  \[**繼續**\] 可讓應用程式繼續執行。  在原生應用程式中，它會導致重新擲回例外狀況。  在 Managed 應用程式中，它會導致程式終止，或是由主控應用程式處理例外狀況。  
  
> [!NOTE]
>  在 Managed 程式碼中發生未處理的例外狀況之後無法繼續執行。  在 Managed 程式碼中發生未處理的例外狀況之後選擇 \[**繼續**\]，將會導致偵錯停止。  
  
 **Ignore**  
 允許繼續執行，而不叫用例外狀況處理常式。  由於不會叫用例外狀況處理常式，因此這會進一步導致包含其他例外狀況和錯誤等後果。  這個選項不適用於某些例外狀況類型。  
  
## 請參閱  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)   
 [例外狀況的最佳作法](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)