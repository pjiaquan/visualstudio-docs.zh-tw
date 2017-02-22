---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugNoSymbolsEvent2 介面"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

訊號[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具使用者介面來警告使用者符號找不到被啟動的可執行檔。  
  
## 語法  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎實作，以及由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具的 UI。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll