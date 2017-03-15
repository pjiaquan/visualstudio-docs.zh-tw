---
title: "如何發覺我的指標是否損毀記憶體位址？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "位址, 指標損毀記憶體位址"
  - "損毀的記憶體位址"
  - "偵錯 [C++], 記憶體損毀"
  - "指標損毀記憶體位址"
  - "記憶體, 損毀"
  - "指標, 損毀記憶體位址"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何發覺我的指標是否損毀記憶體位址？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題說明  
 我認為我的其中一個指標可能損毀在 0x00408000 位址的記憶體。  我該如何確定那裡的狀況？  
  
## 方案  
  
#### 檢查堆積損毀  
  
-   大部分的記憶體損毀實際上是由於堆積損毀所造成。  請嘗試使用全域旗標公用程式 \(gflags.exe\) 或 pageheap.exe。  請參閱 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470)。  
  
#### 若要找出記憶體位址遭修改的位置  
  
1.  在 0x00408000 設定資料中斷點。  請參閱[設定資料變更中斷點 \(僅限原生 C\+\+\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_)。  
  
2.  當您遇到中斷點時，使用 \[**記憶體**\] 視窗來檢視從 0x00408000 開始的記憶體內容。  如需詳細資訊，請參閱[記憶體視窗](../debugger/memory-windows.md)。  
  
## 請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)