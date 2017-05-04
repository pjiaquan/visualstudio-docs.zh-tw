---
title: "IDebugSessionProvider 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSessionProvider 介面"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider 介面
偵錯工具所提供的主要介面 IDE 啟用主機和語言啟始偵錯。  它會執行中應用程式的偵錯工作階段。  這個介面是由機器實作偵錯處理常式。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugSessionProvider` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|初始化具有指定之應用程式的偵錯工作階段。|