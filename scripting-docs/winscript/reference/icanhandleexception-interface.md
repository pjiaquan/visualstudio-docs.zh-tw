---
title: "ICanHandleException 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ICanHandleException 介面"
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException 介面
允許指令碼引擎的呼叫端指定哪些例外狀況呼叫端處理。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`ICanHandleException` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|判斷指令碼引擎的呼叫端是否可以處理指定的例外狀況。|