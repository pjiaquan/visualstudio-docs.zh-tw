---
title: "ISimpleConnectionPoint 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint 介面"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint 介面
提供描述和列舉型別在特定連接點所引發的事件提供簡單的方式。  這個介面也可讓您輕鬆地連接到這些事件的 `IDispatch` 物件。  這個介面是由處理序實作偵錯 Manager \(PDM\) 和使用的指令碼引擎。  
  
 這個介面會從 `IDebugHelper::CreateSimpleConnectionPoint`取得。  
  
 除了繼承自 `IUnknown` 的方法之外，`ISimpleConnectionPoint` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|建立簡單的連接點物件和用戶端的接收之間的連接。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|傳回物件和名稱中的每個事件在事件中指定的範圍。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|傳回在這個介面會公開的事件數目。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|結束先前透過 `ISimpleConnectionPoint::Advise` 建立的諮詢連接。|  
  
## 請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)