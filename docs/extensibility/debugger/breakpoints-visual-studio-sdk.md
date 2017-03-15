---
title: "中斷點 (Visual Studio SDK) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
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
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>中斷點 (Visual Studio SDK)
有三種類型的中斷點︰ 暫止、 繫結和錯誤。  
  
 **暫止的中斷點︰**  
  
-   是包含中斷點繫結至一個或多個程式中的一個或多個程式碼內容所需的所有資訊的抽象概念。 每次程式正在偵錯原因来載入的程式碼的偵錯引擎會檢查以查看是否可以結合所有暫止中斷點。  
  
     暫止中斷點本身永遠不會繫結至程式碼，但會收集而即為包含它所產生的所有繫結的中斷點。  
  
-   由[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
 **繫結的中斷點︰**  
  
-   相關聯或繫結到單一程式碼內容的抽象概念的中斷點。 每個繫結的中斷點會產生暫止中斷點的回應。 暫止中斷點可以不過，產生多個繫結的中斷點。  
  
     卸載程式碼時，就可以解除繫結並捨棄繫結的中斷點。  
  
-   由[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
 **錯誤中斷點︰**  
  
-   是在嘗試將暫止中斷點繫結至程式碼內容描述錯誤的抽象概念。 其中一個錯誤在位置或中斷點運算式本身中說明錯誤中斷點。 如需詳細資訊，請參閱[繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)。  
  
     中斷點錯誤可能是錯誤或警告。  
  
-   由[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
