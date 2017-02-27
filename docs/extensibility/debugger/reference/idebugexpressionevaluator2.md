---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2 介面"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示運算式評估工具 \(EE\) 增強型的版本。  
  
## 語法  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## 實作者注意事項  
 實作這個介面是由運算式評估工具。  
  
## 方法  
 除了在方法 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 介面，這個介面會實作下列方法︰  
  
|方法|描述|  
|--------|--------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|擷取服務物件指定的唯一識別碼。|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|預先載入指定的符號提供者所指定的模組。|  
|[SetCallback](../Topic/IDebugExpressionEvaluator2::SetCallback.md)|可讓運算式評估工具 \(EE\) 來指定偵錯工具引擎 \(DE\) 會用來讀取度量設定回呼介面。|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Common language runtime \(CLR\) 載入偵錯工具中設定的路徑。|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|可讓偵錯引擎在初始化期間，傳遞給運算式評估工具的回呼。|  
|[結束](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|停止並清除運算式評估工具。|  
  
## 需求  
 標頭︰ Ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll