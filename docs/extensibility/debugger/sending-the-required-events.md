---
title: "傳送所需的事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK] 時，所需的事件"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 傳送所需的事件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用本程序所需的事件傳送。  
  
## 傳送必要的事件程序  
 下列的事件為必要欄位，此順序時建立的偵錯引擎 \(DE\) 和附加到程式中：  
  
1.  傳送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 給工作階段的偵錯專案經理 \(SDM\) DE 初始化偵錯的處理序中的一或多個程式時的事件物件。  
  
2.  如果要偵錯的程式附加到，傳送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM 事件物件。  此事件可能會停止事件，您的引擎設計而定。  
  
3.  如果程式附加至處理序啟動時，會傳送 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 為了通知您新的執行緒 IDE SDM 事件物件。  此事件可能會停止事件，您的引擎設計而定。  
  
4.  傳送 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 要 SDM 完成的載入，或當附加至程式完成時偵錯程式時的事件物件。  這個事件，必須停止事件。  
  
5.  如果要偵錯的應用程式啟動時，會傳送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) SDM 將要執行的程式碼在執行階段架構中的第一個指令時，事件物件。  這個事件一定是停止事件。  如果逐步執行偵錯工作階段，IDE 便會停止此事件。  
  
> [!NOTE]
>  許多語言會使用通用的初始設定式或外部，先行編譯的函式 \(來自 CRT 程式庫或 \_Main\) 程式碼的開頭。  如果您正在偵錯的程式語言包含上述任何一種初始的進入點之前的項目，然後執行此程式碼的進入點事件就會傳送當使用者進入點，例如**主要**或`WinMain`，到達。  
  
## 請參閱  
 [啟用偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)