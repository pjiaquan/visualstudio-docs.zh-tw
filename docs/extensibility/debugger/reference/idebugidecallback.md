---
title: "IDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugIDECallback 介面"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 可讓偵錯工具的 \[輸出\] 視窗中顯示訊息的運算式評估工具 \(EE\)。  
  
## 語法  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## 實作者注意事項  
 此回呼是由 managed 偵錯引擎實作。  
  
## 呼叫端資訊  
 它可供將輸出傳送至偵錯工具的 \[輸出\] 視窗的運算式評估工具。  
  
## 方法  
 這個介面會實作下列方法︰  
  
|方法|描述|  
|--------|--------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|將指定的訊息字串傳送至偵錯工具的輸出視窗。|  
  
## 需求  
 標頭︰ Ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll