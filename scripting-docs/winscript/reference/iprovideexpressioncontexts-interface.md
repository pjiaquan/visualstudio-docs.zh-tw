---
title: "IProvideExpressionContexts 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts 介面"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts 介面
提供列舉某些元件已知的運算式內容。  指令碼引擎通常會實作這個介面。  
  
 同處理序偵錯處理常式會使用這個介面會尋找所有全域運算式內容與特定執行緒。  
  
> [!NOTE]
>  這個介面會從執行緒相關的內部。  它是由識別目前執行緒和傳回適當的列舉值的實作決定。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`IProvideExpressionContexts` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|傳回運算式內容的列舉這個元件已知的。|