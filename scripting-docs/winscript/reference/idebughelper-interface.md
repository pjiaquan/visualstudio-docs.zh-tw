---
title: "IDebugHelper 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper 介面"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper 介面
做為 Factory 當做物件瀏覽器和簡單的連接點。  同處理序偵錯 Manager \(PDM\) 實作此介面，以指令碼引擎使用。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugHelper` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|傳回包裝變化的屬性瀏覽器中。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|傳回包裝變化的屬性瀏覽器，並允許不同的 VARTYPE 值或型別的自訂轉換為字串。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|傳回指定 `IDispatch` 包裝物件的事件介面。|