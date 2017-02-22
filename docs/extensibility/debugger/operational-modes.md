---
title: "操作模式 | Microsoft Docs"
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
  - "偵錯引擎模式"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 操作模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

有三種模式當中 IDE 可以運作，，如下所示：  
  
-   [設計模式](#vsconoperationalmodesanchor1)  
  
-   [執行模式](#vsconoperationalmodesanchor2)  
  
-   [中斷模式](#vsconoperationalmodesanchor3)  
  
 您的自訂偵錯引擎 \(DE\) 這些模式之間的轉換方式會要求您先熟悉轉換機制的實作決定。  DE 可能會也可能不會直接實作這些模式。  這些模式其實是偵錯封裝模式切換的使用者動作或來自 DE 事件為基礎。  比方說，來回轉換至中斷模式的執行模式下是從 DE 停止事件所發出的。  中斷\] 來執行巨集模式 」 或 「 步驟 」 模式中來回轉換會引發由使用者執行像是逐步執行\] 或執行的作業。  如需有關 DE 轉換的詳細資訊，請參閱[執行的控制權](../../extensibility/debugger/control-of-execution.md)。  
  
##  <a name="vsconoperationalmodesanchor1"></a> 設計模式  
 設計模式中是 nonrunning 狀態的 Visual Studio 偵錯時，在這段期間您可以設定偵錯應用程式中的功能。  
  
 只有偵幾個錯期間設計模式中所使用的功能。  開發人員可以選擇設定中斷點，或建立監看運算式。  DE 永遠不會載入或 IDE 是在設計模式時呼叫。  DE 互動執行和中斷模式時，會發生。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 執行模式  
 在 IDE 中偵錯工作階段中的程式執行時，就會發生執行的模式。  在應用程式的執行直到結束，直到遇到中斷點，或是會擲回例外狀況。  當終止，DE 會轉換成設計模式中執行應用程式。  當叫用中斷點或發生例外狀況時，DE 轉換成中斷模式。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中斷模式  
 暫停執行偵錯程式時，就會發生中斷模式。  中斷模式提供了開發人員一次的中斷應用程式的快速參考，並可讓開發人員分析應用程式狀態，並變更應用程式執行的方式。  開發人員可以檢視和編輯程式碼、 檢查或修改資料、 重新啟動應用程式、 結束執行，或繼續執行，從相同的點。  
  
 當 DE 傳送同步停止事件時，會輸入中斷模式。  同步停止事件，也稱為 「 停止事件，會通知偵錯叢集 \(SDM\) 與應用程式進行偵錯已停止執行程式碼的 IDE。  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面後，停止事件的範例。  
  
 停止事件，會不斷地延續呼叫下列方法轉換與偵錯工具中斷模式下的執行或逐步執行模式其中一項：  
  
-   [執行](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [逐步執行](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [繼續](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> 步驟 」 模式中  
 當程式帶到下一行程式碼，或插入、 超過預算或者函式時，就會發生步驟 」 模式中。  藉由呼叫方法的步驟執行[逐步執行](../../extensibility/debugger/reference/idebugprocess3-step.md)。  這個方法會要求`DWORD`s 指定的[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)列舉型別做為輸入參數。  
  
 當程式成功地逐步執行至下一行程式碼或執行函式，或執行至游標處，或設定中斷點時，DE 自動轉換回中斷模式。  
  
## 請參閱  
 [執行的控制權](../../extensibility/debugger/control-of-execution.md)