---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker 介面"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

代表自訂使用者介面選取 \[連接埠。  
  
## 語法  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## 實作器注意事項  
 實作這個介面是由連接埠的供應商。  連接埠提供者定義其連接埠選取器，藉由將它公開為 CLSID，並指向`metricPortPickerCLSID`公制在公開的 CLSID。  
  
## 方法  
 下表顯示的方法`IDebugPortPicker`。  
  
|方法|描述|  
|--------|--------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|顯示指定的對話方塊，可讓使用者選取一個連接埠。|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|設定服務提供者。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll