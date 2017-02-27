---
title: "建立自訂的偵錯引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎實作"
  - "偵錯引擎自訂"
  - "偵錯 [偵錯 SDK]，自訂的偵錯引擎"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 建立自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 是一個可讓特定的執行階段架構的偵錯的元件。  通常是只有一個 DE 實作每個執行階段環境。  
  
> [!NOTE]
>  雖然有不同的是實作方式，考慮改用 SQL 和 JScript，VBScript 和 JScript 共用單一 DE。  
  
 將 DE 適用於解譯器或操作系統，以提供執行控制項、 中斷點、 和運算式評估為這種偵錯服務。  這些服務透過 DE 介面實作，而且可能會導致偵錯工具不同的操作模式之間進行轉換。  如需詳細資訊，請參閱 [操作模式](../../extensibility/debugger/operational-modes.md)。  
  
 建立將 DE 包含下列步驟：  
  
1.  註冊 DE Visual Studio  
  
2.  啟用偵錯程式  
  
3.  執行控制及狀態評估  
  
4.  事件傳送  
  
5.  終止，並中斷連結  
  
## 在本節中  
 [註冊自訂的偵錯引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 說明偵錯引擎註冊與 Visual Studio，這樣就可以使用所需的步驟。  
  
 [啟用偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 說明您 DE 可以偵錯程式之前，您必須先啟動 DE 或將它附加至現有的程式。  
  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 討論偵錯應用程式為何需要實作執行控制項功能。  
  
 [傳送事件](../../extensibility/debugger/sending-events.md)  
 說明偵錯工具和 DE 之間的通訊是依據 DCOM 的事件模型。  
  
 [終止，並中斷連結](../../extensibility/debugger/termination-and-detaching.md)  
 說明如何達成這表示沒有任何中斷點、 例外狀況、 執行階段錯誤或要偵錯應用程式中的無限迴圈的正常結束。  
  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)  
 文件的偵錯工作階段中發生的事件呼叫的順序。  
  
 [How To: 偵錯自訂的偵錯引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 說明如何偵錯自訂 DE。  
  
## 請參閱  
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)