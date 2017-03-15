---
title: "例外狀況處理 (Visual Studio SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，例外狀況處理"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 例外狀況處理 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明擲回例外狀況時，就會發生的處理程序。  
  
## 例外狀況的處理程序  
  
1.  當第一次擲回例外狀況時，但它由例外處理常式，以進行偵錯程式中處理之前，偵錯引擎 \(DE\) 便會將 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 工作階段偵錯管理員 \(SDM\) 為 「 停止 」 事件。  `IDebugExceptionEvent2`要是例外狀況 \(在偵錯在封裝中的例外規則\] 對話方塊中指定\) 的設定可指定使用者想要停止在第一個出現的例外狀況通知會傳送。  
  
2.  SDM 呼叫 [IDebugExceptionEvent2::GetException](../Topic/IDebugExceptionEvent2::GetException.md) 以取得例外狀況的屬性。  
  
3.  偵錯的封裝呼叫 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 來判斷哪些選項呈現給使用者。  
  
4.  偵錯封裝會詢問使用者如何藉由開啟第一個出現的例外狀況\] 對話方塊來處理例外狀況。  
  
5.  如果使用者選擇要繼續，SDM 會呼叫 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。  
  
    -   如果這個方法會傳回 S\_OK，會呼叫 [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。  
  
         \-或\-  
  
         如果這個方法傳回 S\_FALSE，程式進行偵錯有機會第二個來處理例外狀況。  
  
6.  如果正在進行偵錯的程式沒有為第二個可能的例外狀況的處理常式，會傳送 DE `IDebugExceptionEvent2`來為 SDM  **EVENT\_SYNC\_STOP**。  
  
7.  偵錯封裝會詢問使用者如何藉由開啟第一個出現的例外狀況\] 對話方塊來處理例外狀況。  
  
8.  偵錯的封裝呼叫 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 來判斷哪些選項呈現給使用者。  
  
9. 偵錯封裝會詢問使用者如何藉由開啟第二個可能的例外狀況\] 對話方塊來處理例外狀況。  
  
10. 如果這個方法會傳回 S\_OK，會呼叫`IDebugExceptionEvent2::PassToDebuggee`。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)