---
title: "IDebugStackFrameSniffer 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer 介面"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer 介面
提供列舉型別 \(Enumeration\) 元件已知的邏輯堆疊框架。  指令碼引擎通常會實作這個介面。  同處理序偵錯處理常式會使用這個介面會尋找所有堆疊框架與特定執行緒。  
  
> [!NOTE]
>  偵錯工具會呼叫這個介面會從執行緒相關的內部。  指令碼引擎必須識別目前執行緒和傳回適當的列舉值。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`IDebugStackFrameSniffer` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|傳回堆疊框架的列舉值目前執行緒的。|