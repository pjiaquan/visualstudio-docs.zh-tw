---
title: "錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視以不同使用者執行 | Microsoft Docs"
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
  - "anyuser 選項"
  - "-anyuser 選項"
  - "msvsmon.exe"
  - "遠端偵錯監視器"
  - "遠端偵錯, 遠端偵錯監視器"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視以不同使用者執行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。  
  
## 原因  
 當您以 \[非驗證\] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。  
  
## 解決方案  
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 \(msvsmon.exe\) 和 Visual Studio。  如果無法這麼做的話，您可以使用其他帳戶執行遠端偵錯監視，方法是在遠端偵錯監視的 \[**選項**\] 對話方塊中選取 \[**允許任何使用者執行偵錯**\] 選項。  
  
> [!CAUTION]
>  將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。  以 \[**非驗證**\] 模式進行偵錯非常不安全，請務必小心使用。  
  
 如需詳細資訊，請參閱[啟動遠端偵錯監視](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)。  
  
## 請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)