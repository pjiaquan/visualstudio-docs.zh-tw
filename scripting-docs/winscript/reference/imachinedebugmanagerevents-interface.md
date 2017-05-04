---
title: "IMachineDebugManagerEvents 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerEvents 介面"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents 介面
在電腦所維護之執行中的應用程式清單上的信號變更偵錯處理常式。  這個介面可由偵錯工具 IDE 是用來顯示應用程式的動態清單。  
  
 除了繼承自 `IUnknown` 的方法之外，`IMachineDebugManagerEvents` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|指出應用程式加入至執行中的應用程式清單時，處理事件。|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|當應用程式執行應用程式的清單中移除時，處理事件。|