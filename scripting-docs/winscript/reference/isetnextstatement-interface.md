---
title: "ISetNextStatement 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement 介面
這個介面是由解譯器實作允許進行偵錯的處理常式會更新目前的陳述式。  它會從堆疊框架物件實作，因此， PDM 透過 QueryInterface 取得這個介面。  
  
 介面提供設定執行點很有用，決定要執行的下一個陳述式的方法。  
  
 除了繼承自 `IUnknown` 的方法之外，`ISetNextStatement` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|判斷執行點是否可以設定為指定的位置。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|設定執行點至指定的位置。|