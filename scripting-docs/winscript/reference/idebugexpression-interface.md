---
title: "IDebugExpression 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression 介面"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression 介面
表示非同步評估的運算式。  指令碼引擎通常會實作這個介面。  偵錯工具 IDE 通常會使用這個介面可讓某個立即執行視窗或 \[監看式\] 視窗。  
  
> [!NOTE]
>  `IDebugExpression` 介面從堆疊框架才有。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugExpression` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|啟動這個運算式的評估。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|中止此運算式。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|判斷作業是否已完成。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|傳回運算式評估結果為字串和作業的傳回值。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|傳回運算式評估的結果做為偵錯屬性和作業的傳回值。|