---
title: "IEnumDebugStackFrames 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IEnumDebugStackFrames 介面"
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames 介面
列舉型別 \(Enumeration\) 堆疊框架與執行緒對應。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`IEnumDebugStackFrames` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|擷取區段的指定數目在列舉型別序列中|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|略過區段的指定數目在列舉型別序列中|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|將列舉序列重設到開頭。|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|建立列舉程式，其中包含與目前列舉程式相同的狀態。|