---
title: "IDebugAlias2 | Microsoft Docs"
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
  - "IDebugAlias2 介面"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 代表別名數值變數，並可讓運算式評估工具 \(EE\) 來取得應用程式定義域做為別名。  
  
## 語法  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## 實作者注意事項  
 實作這個介面是由 managed 偵錯引擎 \(DE\)。  
  
## 方法  
 除了在方法 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 介面，這個介面會實作下列方法︰  
  
|方法|描述|  
|--------|--------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|擷取應用程式定義域的識別項。|  
  
## 備註  
 別名是以字串形式加上 \# 字元，例如 1001 \# 的十進位數字。  
  
## 需求  
 標頭︰ Ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll