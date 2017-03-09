---
title: "偵錯 ASP.NET 和 AJAX 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "偵錯 [ASP.NET], 關於 ASP.NET 偵錯"
  - "偵錯 ASP.NET Web 應用程式"
  - "偵錯, WCF"
  - "WCF, 偵錯"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯 ASP.NET 和 AJAX 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式類似偵錯 Windows Form 或任何其他 Windows 應用程式，因為這兩種應用程式都涉及控制項和事件。  但是，兩種應用程式之間仍然有基本差異：  
  
-   在 Web 應用程式中持續追蹤狀態是更複雜的。  
  
-   在 Windows 應用程式中，要偵錯的程式碼大部分都在同一個位置；而在 Web 應用程式中，程式碼則可以在用戶端和伺服器上。  當 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式碼全部都在伺服器時，用戶端可能也會有 JavaScript 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 程式碼。  
  
## 在本節中  
 [準備偵錯 ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 說明啟用 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式偵錯的必要步驟。  
  
 [偵錯 Web 應用程式](../debugger/debugging-web-applications.md)  
 討論如何偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式，包括已啟用 AJAX 功能的指令碼應用程式。  
  
## 相關章節  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)  
 說明必須啟用 Just My Code 以便偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況的原因。  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 討論一些可幫助您進行 AJAX 程式碼偵錯的技術和工具。  
  
 [使用 IntelliTrace](../debugger/intellitrace.md)  
 使用 IntelliTrace 記錄和檢視您的應用程式狀態記錄，可讓您更快速地進行程式碼偵錯，而不需要經常重新啟動應用程式。  您可以查看應用程式執行期間發生的事件和呼叫相關資訊，並且從這些時間點開始進行偵錯。  需要 Visual Studio Ultimate。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)