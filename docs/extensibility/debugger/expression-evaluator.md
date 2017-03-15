---
title: "運算式評估工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式 [偵錯 SDK]"
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# 運算式評估工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

運算式評估工具 \(EE\) 檢查一種語言來剖析和執行階段評估變數和運算式的語法，讓他們 IDE 是在中斷模式時，使用者可以檢視。  
  
## 使用運算式評估工具  
 運算式用來建立[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，如下所示：  
  
1.  偵錯引擎 \(DE\) 實作[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  
  
2.  偵錯封裝取得`IDebugExpressionContext2`獲取[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，然後呼叫`IDebugStackFrame2::ParseText`方法，以取得[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。  
  
3.  偵錯的封裝呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法或[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法來取得運算式的值。  `IDebugExpression2::EvaluateAsync`是從命令\/即時運算\] 視窗時所呼叫的方法。  其他所有 UI 元件都呼叫`IDebugExpression2::EvaluateSync`。  
  
4.  運算式評估的結果是[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，其中包含名稱、 類型和值的運算式評估的結果。  
  
 運算式評估期間得知 ee 給予會要求從符號的提供者元件的資訊。  符號提供者會提供用來識別及瞭解剖析的運算式所使用的符號資訊。  
  
 完成非同步運算式評估時，非同步事件傳送到工作階段偵錯管理員 \(SDM\) DE 通知運算式評估是完整的 IDE。  完成同步的運算式評估時，評估的結果會傳回，呼叫`IDebugExpression2::EvaluateSync`方法。  
  
## 實作的注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎預期要與使用通用語言執行階段 \(CLR\) 介面的運算式評估工具。  如此一來，運算式評估工具，適用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎都必須支援 CLR \(所有的 CLR 偵錯介面的完整清單，請參閱 debugref.doc，也就是組件的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]\)。  
  
## 請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)