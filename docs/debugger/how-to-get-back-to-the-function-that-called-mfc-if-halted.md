---
title: "如何：如果暫止，回到呼叫 MFC 的函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "中斷命令"
  - "偵錯 [MFC], 函式"
  - "偵錯 [MFC], 回到呼叫函式"
  - "函式呼叫, 回到呼叫函式"
  - "函式 [C++], 偵錯"
  - "函式 [偵錯工具]"
  - "程式, 暫止"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：如果暫止，回到呼叫 MFC 的函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[工具\] 功能表中選取 \[匯入和匯出設定\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 如果您使用 \[**偵錯**\] 功能表上的 \[**中斷**\] 命令來暫止程式並於 MFC 中結束，而且您確定問題位於程式碼時，可以使用 \[呼叫堆疊\] 視窗巡覽回該函式。  如需詳細資訊，請參閱 [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。  
  
 有時候，您的程式碼可能會在訊息幫浦內中斷。  如果發生這種情形，呼叫堆疊上不會有任何使用者程式碼。  若要避免發生此問題，您可以改用中斷點 \(可能含條件與叫用次數\) 來取代 \[**中斷**\] 命令。  如需詳細資訊，請參閱[Breakpoints and Tracepoints](http://msdn.microsoft.com/zh-tw/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
### 若要巡覽至呼叫 MFC 的函式  
  
-   使用 \[**呼叫堆疊**\] 視窗。  
  
## 請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)