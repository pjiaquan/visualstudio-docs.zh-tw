---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "IDebugAlias 介面"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 代表變數的數字的別名。 別名是變數只是不同的名稱。  
  
## 語法  
  
```  
IDebugAlias : IUnknown  
```  
  
## 實作者注意事項  
 運算式評估工具 \(EE\) 會實作這個介面可支援數值的別名變數。  
  
## 呼叫端資訊  
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md) 建立特定物件的別名。 若要搜尋的別名，請使用 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 或 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。  
  
## 依照 Vtable 順序的方法  
 下列方法會定義在 `IDebugAlias` 介面。  
  
|方法|描述|  
|--------|--------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|取得這個別名所參考的物件。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|取得別名名稱。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|擷取 `ICorDebugValue` 介面，可用來存取管理此物件 \(僅限 managed 程式碼\) 的程式碼資訊。|  
|[處置](../../../extensibility/debugger/reference/idebugalias-dispose.md)|將此標示別名為不再使用。|  
  
## 備註  
 別名是以字串形式加上 \# 字元，例如 1001 \# 的十進位數字。  
  
## 需求  
 標頭: ee.h  
  
 命名空間: Microsoft.VisualStudio.Debugger.Interop  
  
 組件: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)