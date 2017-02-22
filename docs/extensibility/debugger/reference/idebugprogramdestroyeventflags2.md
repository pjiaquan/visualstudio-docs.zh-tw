---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
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
  - "IDebugProgramDestroyEventFlags2 介面"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟用偵錯引擎來覆寫預設行為的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI，當您結束偵錯工作階段。  
  
## 語法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由偵錯引擎。  很有用的主機，可能會建立並終結多個程式的處理序存留期。  
  
## 方法  
 下表顯示的方法`IDebugProgramDestroyEventFlags2`。  
  
|方法|描述|  
|--------|--------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|擷取程式摧毀旗標。|  
  
## 備註  
 預設行為的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 是以返回設計模式後所有的程式已派遣程式損毀事件。  這個介面會啟用偵錯引擎來變更該行為。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll