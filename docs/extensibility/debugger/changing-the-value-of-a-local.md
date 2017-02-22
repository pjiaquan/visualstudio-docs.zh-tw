---
title: "變更本機值 | Microsoft Docs"
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
  - "偵錯的 [偵錯 SDK]，運算式評估"
  - "運算式評估，以程式設計方式變更值"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 變更本機值
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當新的值型別中的值欄位 **區域變數** \] 視窗中，偵錯封裝會將字串傳遞，因為運算式評估工具 \(EE\) 型別。 EE 評估此字串，其中可以包含簡單的值或運算式，並將產生的值儲存在相關聯的本機。  
  
 這是變更本機值的程序的概觀︰  
  
1.  使用者輸入新值之後，Visual Studio 會呼叫 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 上 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 本機相關聯的物件。  
  
2.  `IDebugProperty2::SetValueAsString` 執行下列工作︰  
  
    1.  評估用來產生值的字串。  
  
    2.  繫結相關聯 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件來取得 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件。  
  
    3.  將值轉換成一系列的位元組。  
  
    4.  呼叫 [Setvalue 巨集](../Topic/IDebugObject::SetValue.md) 將值的位元組放入記憶體，以便進行偵錯的程式可以存取它們。  
  
3.  Visual Studio 會重新整理 **區域變數** 顯示 \(請參閱 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md) 如需詳細資訊\)。  
  
 此程序也用來變更中的變數值 **監看式** 除了它是 `IDebugProperty2` 物件相關聯的值來取代本機 `IDebugProperty2` 本機本身相關聯的物件。  
  
## 本章節內容  
 [變更值的範例實作](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 使用 MyCEE 範例來逐步完成變更值的程序。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md)