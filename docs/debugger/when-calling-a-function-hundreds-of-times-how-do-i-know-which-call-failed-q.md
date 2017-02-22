---
title: "呼叫函式好幾百次時，如何判斷是哪一個呼叫失敗？ | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "中斷點, 疑難排解"
  - "條件中斷點"
  - "錯誤 [偵錯工具], 尋找哪一個函式呼叫失敗"
  - "錯誤 [偵錯工具], 函式呼叫"
  - "錯誤 [Visual Studio], 函式呼叫"
  - "失敗"
  - "函式呼叫, 失敗"
  - "函式 [偵錯工具]"
  - "叫用次數"
  - "位置中斷點呼叫失敗"
  - "略過次數"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 呼叫函式好幾百次時，如何判斷是哪一個呼叫失敗？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題說明  
 我的程式在呼叫某個函式 \(`CnvtV`\) 時失敗。  失敗之前，程式大概會呼叫此函式幾百次。  如果我在 `CnvtV` 上設定一個中斷點，程式會在每次呼叫此函式時停止，但是我不要這樣。  我不知道什麼條件會造成呼叫失敗，因此我無法設定條件中斷點。  我該怎麼做？  
  
## 方案  
 您可以在函式上設定一個 \[**叫用次數**\] 欄位值永遠無法遇到的中斷點。  在這種情況下，因為您相信函式 `CnvtV` 會遭呼叫幾百次，請將 \[**叫用次數**\] 設為 1000 或更高。  接著執行程式並且等候它失敗。  當程式失敗時，開啟 \[中斷點\] 視窗並且查看中斷點的清單。  您在 `CnvtV` 上設定的中斷點會出現，其後跟著叫用次數和未完成的重複運算次數：  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 現在您已經知道函式會在第 101 次呼叫時失敗。  如果您以叫用次數 101 重設中斷點並且再次執行程式，程式會在上次造成失敗的 `CnvtV` 呼叫處停止。  
  
## 請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/zh-tw/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [偵錯機器碼](../debugger/debugging-native-code.md)