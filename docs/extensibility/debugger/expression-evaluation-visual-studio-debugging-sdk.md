---
title: "運算式評估 (Visual Studio 偵錯 SDK) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 68773ccac304972f4d96642a226a586d69efb783
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio 偵錯 SDK)
在中斷模式期間 IDE 必須包含數個變數的程式的簡單運算式進行評估。 若要這麼做，偵錯引擎 (DE) 必須能夠剖析及評估在 IDE 的視窗中輸入的運算式。  
  
 運算式建立使用[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，是由所產生的[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
 **IDebugExpression2**介面的實作方法 DE 並呼叫其**EvalAsync**方法來傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面的 ide，以顯示在 IDE 中的運算式評估的結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回可用於運算式的值放到 監看式視窗或 [區域變數] 視窗的結構。  
  
 偵錯封裝或工作階段偵錯管理員 (SDM) 呼叫[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面，表示評估的結果。 `IDebugProperty2`已傳回名稱、 類型和運算式的值的方法。 這項資訊會顯示在各種偵錯工具視窗。  
  
## <a name="using-expression-evaluation"></a>使用運算式評估  
 若要使用運算式評估，您必須實作[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法及其所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，如下列表格所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步的方式來評估運算式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式來評估運算式。|  
  
 同步和非同步評估要求的實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 非同步運算式評估要求實作[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
