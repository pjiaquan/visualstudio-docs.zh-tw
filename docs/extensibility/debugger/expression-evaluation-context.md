---
title: "運算式評估內容 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估、 內容"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 運算式評估內容
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯時， **運算式評估內容**：  
  
-   表示運算式評估內容。  一般而言，評估內容相對於內用來評估變數、 參數、 函式，以及方法的語彙範圍。  比方說，堆疊框架相關聯，運算式評估內容將提供的內容，來評估區域變數、 方法參數和類別成員 \(如果有的話\)。  
  
-   當程式已經停止於中斷點時，就會存在。  運算式本身是一種資料結構，表示剖析的運算式可準備進行繫結，並評估指定的內容中。  
  
     更多細節而言，運算式建立使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。  評估運算式時，就會產生可列印的字串，包含名稱和型別的變數或引數和它的值。  這個字串會顯示在 \[監看式\] 視窗或 IDE 的 \[區域變數\] 視窗中。  
  
     提供`BSTR`和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，可以建立偵錯引擎 \(DE\) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面剖析運算式。  提供`IDebugExpression2`介面，DE 能夠透過同步或非同步運算式評估的值。  這個值，和名稱和型別的變數或引數，會傳給 IDE 進行顯示。  
  
## 請參閱  
 [運算式評估介面](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)