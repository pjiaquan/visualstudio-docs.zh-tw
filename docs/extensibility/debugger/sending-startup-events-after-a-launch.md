---
title: "在啟動後傳送啟動事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，啟動事件"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 在啟動後傳送啟動事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

一旦偵錯引擎 \(DE\) 附加到該程式時，它會將一系列的啟動事件送回偵錯工作階段中。  
  
 啟動事件傳送到偵錯工作階段包括下列各項：  
  
-   引擎建立事件。  
  
-   程式建立的事件。  
  
-   執行緒建立與模組載入事件。  
  
-   載入完成事件，傳送載入並準備好執行時，程式碼時，但在執行任何程式碼  
  
    > [!NOTE]
    >  當這個事件會繼續之後時，會初始化全域變數，然後啟動常式執行。  
  
-   請盡量其他執行緒建立與模組載入事件。  
  
-   進入點事件，即表示該程式已到達它的主要進入點，例如**主要**或`WinMain`。  如果是附加至正在執行的程式，不是通常傳送這個事件。  
  
 以程式設計的方式，是先傳送工作階段偵錯管理員 \(SDM\)  [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面，它代表引擎建立事件，後面加上 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)，用來表示程式建立事件。  
  
 這通常是後面會有一個以上 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 執行緒建立事件和 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 模組載入事件。  
  
 當程式碼已載入並準備好執行時，但會執行任何程式碼之前，會在下列情況中 DE 傳送 SDM  [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 載入完成的事件。  最後，如果沒有執行 \[程式\]，會將 DE 傳送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 進入點的事件，通知程式已到達它的主要進入點，並已準備好進行偵錯。  
  
## 請參閱  
 [執行的控制權](../../extensibility/debugger/control-of-execution.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)