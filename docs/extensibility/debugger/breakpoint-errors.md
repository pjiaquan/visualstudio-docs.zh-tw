---
title: "中斷點錯誤 | Microsoft Docs"
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
  - "錯誤的中斷點"
  - "偵錯的 [偵錯 SDK]，中斷點錯誤"
  - "錯誤 [偵錯 SDK]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 中斷點錯誤
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明的程序時中斷點會嘗試繫結至程式碼，但失敗：  
  
## 疑難排解中斷點時發生錯誤  
  
1.  偵錯引擎 \(DE\) 傳送 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 給工作階段的偵錯專案經理 \(SDM\)。  
  
2.  SDM 呼叫 [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 貴`ppErrorBP`\) 以取得錯誤的中斷點。  
  
3.  SDM 呼叫 [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) 以取得錯誤中斷點起始處的暫止中斷點。  
  
4.  SDM 呼叫 [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 以取得錯誤中斷點要繫結失敗的原因。  
  
## 請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)