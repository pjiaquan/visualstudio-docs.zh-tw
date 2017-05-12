---
title: "IDebugSessionProviderEx 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSessionProviderEx 介面
主要介面由偵錯工具整合式開發環境 \(IDE\) 提供啟用主人和語言啟始偵錯。  它會執行中應用程式的偵錯工作階段。  這個介面是由機器實作偵錯處理常式。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugSessionProviderEx` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|判斷提示的偵錯是否為指定的應用程式。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|初始化具有指定之應用程式的偵錯工作階段。|