---
title: "逐步解說：在設計階段進行偵錯 | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "中斷點, 設計階段偵錯"
  - "偵錯 [Visual Studio], 設計階段"
  - "設計階段偵錯"
  - "即時運算視窗, 設計階段偵錯"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 逐步解說：在設計階段進行偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

應用程式沒有在執行時，您可以使用 Visual Studio \[**即時運算**\] 視窗來執行函式或副程式。  如果函式或副程式含有中斷點，Visual Studio 就會在適當的點中斷執行。  然後，您就可以使用偵錯工具視窗來檢查程式的狀態。  這個功能在設計階段稱為偵錯。  
  
 下列程序向您示範如何使用這個功能。  
  
### 若要從即時運算視窗叫用中斷點  
  
1.  將下列程式碼貼到 Visual Basic 主控台應用程式：  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  在顯示 `s="Add BreakPoint Here"` 的那一行設定中斷點。  
  
3.  在下列 \[**即時運算**\] 視窗中輸入：`?MyFunction<enter>`  
  
4.  確認已叫用中斷點，並且呼叫堆疊是正確的。  
  
5.  在 \[**偵錯**\] 功能表上，按一下 \[**繼續**\]，並確認您仍在設計模式中。  
  
6.  在下列 \[**即時運算**\] 視窗中輸入：`?MyFunction<enter>`  
  
7.  在 \[**即時運算**\] 視窗中輸入下列：`?MySub<enter>`  
  
8.  確認已叫用中斷點，並檢查 \[**區域變數**\] 視窗中靜態變數 `i` 的值。  該變數的值應該是 3。  
  
9. 確認呼叫堆疊是正確的。  
  
10. 在 \[**偵錯**\] 功能表上，按一下 \[**繼續**\]，並確認您仍在設計模式中。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)