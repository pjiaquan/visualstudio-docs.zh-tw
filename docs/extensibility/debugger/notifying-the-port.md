---
title: "通知連接埠 | Microsoft Docs"
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
  - "連接埠通知"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 通知連接埠
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在啟動程式之後, 的連接埠必須被告知，，如下所示：  
  
1.  當連接埠接收到新的 \[程式\] 節點時，其會傳送回偵錯工作階段的程式建立事件。  事件會具有代表程式的介面。  
  
2.  偵錯工作階段查詢可以附加至偵錯引擎 \(DE\) 的識別項的程式。  
  
3.  偵錯工作階段會檢查看看 DE 是否允許 DEs，該程式的清單上。  偵錯工作階段取得這份清單從原本由偵錯封裝傳遞給它的方案的作用中的程式設定。  
  
     DE 必須在 \[允許\] 清單中，否則 DE 就不會附加到程式。  
  
 以程式設計的方式，當連接埠第一次收到新的 \[程式\] 節點，它會建立 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ，表示該程式的介面。  
  
> [!NOTE]
>  這不應該混淆與`IDebugProgram2`稍後由偵錯引擎 \(DE\) 的介面。  
  
 連接埠傳送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 回工作階段偵錯管理員 \(SDM\) 的 COM 的程式建立事件`IConnectionPoint`介面。  
  
> [!NOTE]
>  這不應該混淆與`IDebugProgramCreateEvent2` DE 稍後傳送的介面。  
  
 事件介面本身一起傳送連接埠 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)，  [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)，以及  [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 分別代表連接埠、 處理序和程式的介面。  SDM 呼叫 [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) 以取得可以偵錯程式 DE 的 GUID。  GUID 原本來自 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 介面。  
  
 SDM 會檢查看看 DE 是否允許 DEs 的清單上。  SDM 會取得這份清單，從原本由偵錯封裝傳遞給它的方案的作用中的程式設定。  DE 必須在 \[允許\] 清單中，否則就不會附加到程式。  
  
 一旦知道 DE 的識別身份，SDM 還將其附加到程式。  
  
## 請參閱  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)   
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)