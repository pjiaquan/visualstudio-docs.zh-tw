---
title: "如何：偵錯 OnStart 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "OnStart 方法"
  - "偵錯 [Visual Studio], 視窗服務"
  - "偵錯 Managed 程式碼, OnStart 方法"
  - "偵錯 Windows 服務應用程式, OnStart 方法"
  - "Windows 服務應用程式, 偵錯"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：偵錯 OnStart 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以藉由啟動服務並將偵錯工具附加到服務處理序，對 Windows 服務進行偵錯。 如需詳細資訊，請參閱[如何：偵錯 Windows 服務應用程式](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)。 但是若要對 Windows 服務的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> 方法進行偵錯，您必須從方法內啟動偵錯工具。  
  
1.  在 `OnStart()` 方法的開頭加入對 <xref:System.Diagnostics.Debugger.Launch%2A> 的呼叫。  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  啟動服務 \(您可以使用 `net start`，或在 \[服務\] 視窗中加以啟動\)。  
  
     您應該會看到如下所示的對話方塊：  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  選取 \[是，對 \<服務名稱\> 進行偵錯\]。  
  
4.  在 \[Just\-In\-Time 偵錯工具\] 視窗中，選取您要用來偵錯的 Visual Studio 版本。  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Visual Studio 的新執行個體隨即啟動，並在 `Debugger.Launch()` 方法停止執行。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)