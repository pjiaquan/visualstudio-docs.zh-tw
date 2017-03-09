---
title: "例外狀況之後繼續執行 | Microsoft Docs"
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
  - "偵錯工具, 例外狀況"
  - "例外狀況處理, 繼續執行"
  - "例外狀況對話方塊"
  - "例外狀況, 繼續執行"
  - "執行, 例外狀況之後繼續"
  - "Managed 程式碼, 例外狀況處理"
  - "Managed 例外狀況, 繼續執行"
  - "程式執行"
  - "程式, 執行"
  - "執行緒處理 [Visual Studio], 例外狀況之後繼續執行"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 例外狀況之後繼續執行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當偵錯工具因為例外狀況而中斷執行時，對話方塊隨即出現。  若是在 Visual Basic 或 C\# 中，根據預設您會看到[Exception Assistant](../Topic/Exception%20Assistant.md)對話方塊。  若是在 C\+\+ 中，您會看到舊版的 \[**例外狀況**\] 對話方塊。  如果您使用的是 Visual Basic 或 C\#，但已停用 \[**選項**\] 對話方塊中的 \[**例外狀況助理**\]，您就會看到 \[**例外狀況**\] 對話方塊。  
  
 當 \[**例外狀況助理**\] 或 \[**例外狀況**\] 對話方塊出現時，您可以嘗試修正造成例外狀況的問題。  
  
## Managed 程式碼  
 在 Managed 程式碼中，您可以在出現未處理的例外狀況之後，繼續在相同的執行緒中執行。  \[**例外狀況助理**\] 會將呼叫堆疊回溯至擲回例外狀況的位置。  
  
## 機器碼  
 在原生 C\/C\+\+ 中，您擁有兩個選項：  
  
-   您可以按一下 \[**中斷**\] 並嘗試修正問題。  在中斷模式中，您可以用滑鼠右鍵按一下 \[**呼叫堆疊**\] 視窗中的框架，並在捷徑功能表中選取 \[**回溯至此框架**\]，藉此回溯呼叫堆疊。  繼續進行偵錯時，如果問題並未修正，\[**例外狀況**\] 對話方塊就會再次出現。  如果已修正問題，\[**例外狀況**\] 對話方塊就不會再次出現。  
  
-   您可以按一下 \[**繼續**\] 繼續執行，而不嘗試修正問題。  \[**例外狀況**\] 對話方塊會再次出現。  
  
## 混合程式碼  
 如果在偵錯原生和 Managed 混合的程式碼時發生未處理的例外狀況，作業系統條件約束會禁止回溯呼叫堆疊。  如果您嘗試使用捷徑功能表回溯呼叫堆疊，就會出現錯誤訊息，說明在混合程式碼偵錯期間，偵錯工具無法從未處理的例外狀況回溯。  
  
## 請參閱  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)