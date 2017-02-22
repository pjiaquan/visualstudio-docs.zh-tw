---
title: "啟動程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎啟動"
  - "啟動程式"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 啟動程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

想要偵錯程式使用者可以按下 F5 以執行偵錯工具從 IDE。  這一開始一系列的事件，且最終會造成 IDE 的連線到偵錯引擎 \(DE\)，它是依序連接，或是附加至程式，如下所示：  
  
1.  IDE 會先呼叫專案套件，以取得使用中專案的方案的偵錯設定。  設定包括起始目錄、 環境變數、 連接埠的程式會執行，以及用於建立該程式，如果指定 DE。  這些設定值會傳遞至偵錯的封裝。  
  
2.  如果指定的是，DE 呼叫作業系統來啟動程式。  啟動程式的載入程式的執行階段環境。  比方說，如果程式在 MSIL 中撰寫，公用語言執行時間也會叫用執行程式。  
  
     \-或\-  
  
     如果未指定的是，連接埠就會呼叫以啟動程式，這可以讓要載入的程式的執行階段環境的作業系統。  
  
    > [!NOTE]
    >  如果將 DE 被用來啟動程式，可能是相同的 DE 就會附加到程式。  
  
3.  取決於是否 DE 或連接埠啟動程式，DE 或執行階段環境會建立應用程式的說明或節點，然後通知程式執行時的連接埠。  
  
    > [!NOTE]
    >  最好是在執行階段環境建立 \[程式\] 節點中，因為程式節點是一種程式，才能進行偵錯的輕量級表示。  並不需要載入整個 DE 只是為了建立並登錄程式\] 節點。  如果是設定為在 IDE 中，但沒有可用的 IDE 的程序中執行實際執行，需要有一種元件，可以將程式的節點加到連接埠。  
  
 新建立的程式，以及與任何其他程式，與相關或不相關的、 啟動或附加至相同的 IDE 中，從撰寫偵錯工作階段。  
  
 以程式設計的方式，當使用者第一次按 **F5**， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的偵錯封裝呼叫專案封裝 \(也就是相關聯的啟動程式的型別\) 透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法，依序填寫<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>與解決方案的使用中專案的偵錯設定結構。  這個結構時，會傳回至偵錯封裝上，透過呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>方法。  偵錯套件再具現化工作階段的偵錯管理員 \(SDM\)，這會開啟程式進行偵錯，以及任何關聯的偵錯引擎。  
  
 SDM 傳入的引數是要用來啟動程式 DE 的 GUID。  
  
 如果不是 DE GUID `GUID_NULL`，SDM 會同時建立的是，接著再呼叫其[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法，以啟動程式。  例如，如果程式以機器碼撰寫，然後`IDebugEngineLaunch2::LaunchSuspended`可能會呼叫`CreateProcess`和`ResumeThread` \(Win32 函式\)，來執行程式。  
  
 啟動程式的載入程式的執行階段環境。  然後建立 DE 或執行階段環境[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面來描述該程式，並將這個介面來[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)來通知程式執行時的連接埠。  
  
 如果`GUID_NULL`被傳遞時，然後連接埠啟動程式。  一旦應用程式，執行階段環境就會建立`IDebugProgramNode2`介面來描述該程式，並將它傳遞`IDebugPortNotify2::AddProgramNode`。  這樣便會通知程式執行時的連接埠。  然後 SDM 會將偵錯引擎附加至正在執行的程式。  
  
## 本章節內容  
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)  
 說明在啟動程式，並通知連接埠之後，會發生什麼事。  
  
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)  
 當偵錯工作階段已準備好將 DE 附加到程式的文件。  
  
## 相關章節  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種偵錯工作的詳細資訊，例如啟動的程式，並評估運算式的連結。