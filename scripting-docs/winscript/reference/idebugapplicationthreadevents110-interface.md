---
title: "IDebugApplicationThreadEvents110 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 介面"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 介面
加入更多執行緒處理事件。  這些事件只區域。  也就是您可以訂閱只能在 [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) 以通知偵錯，處理序，並在 PDM 應用程式的 unadvise 方法執行緒物件 \(實作 [IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)\) 的物件。  這些執行緒中發生這些來源。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IDebugActivationThreadEvents110` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|將呼叫加入到使用 PDM 的執行緒切換執行緒中啟動。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|執行緒從中斷點復原，然後再次為作用中。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|執行緒在中斷點停止回應浮點數，並且可以處理執行緒完全逾時的呼叫。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|將呼叫加入到使用 PDM 的執行緒切換執行緒中完成。|