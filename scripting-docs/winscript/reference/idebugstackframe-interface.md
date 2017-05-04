---
title: "IDebugStackFrame 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame 介面"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame 介面
表示在執行緒堆疊的邏輯堆疊框架。  呼叫 `IDebugStackFrame::QueryInterface` 方法取得 `IDebugExpressionContext` 介面，可讓運算式評估並檢視視窗。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugStackFrame` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|傳回目前程式碼內容與堆疊框架。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|傳回堆疊框架的簡短或完整的文字描述。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|傳回這種語言中的簡短或完整的文字描述。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|會傳回執行緒與此堆疊框架。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|傳回目前框架的屬性瀏覽器。|