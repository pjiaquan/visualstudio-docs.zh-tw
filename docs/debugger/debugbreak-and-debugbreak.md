---
title: "DebugBreak 和 __debugbreak | Microsoft Docs"
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
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "中斷點, DebugBreak 函式"
  - "DebugBreak 函式"
  - "偵錯 [C++], DebugBreak 函式"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DebugBreak 和 __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在程式碼中的任何一點呼叫 DebugBreak Win32 函式或 [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) 內建。  `DebugBreak` 和 `__debugbreak` 的作用與在該位置設定中斷點的作用相同。  
  
 由於 `DebugBreak` 屬於系統函式呼叫，因此必須安裝系統偵錯符號，才能確保中斷後會顯示正確的呼叫堆疊資訊。  否則，偵錯工具所顯示的呼叫堆疊資訊可能會偏移一個框架。  如果您使用 `__debugbreak`，就不需要符號。  
  
## 請參閱  
 [編譯器內建](/visual-cpp/intrinsics/compiler-intrinsics)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)