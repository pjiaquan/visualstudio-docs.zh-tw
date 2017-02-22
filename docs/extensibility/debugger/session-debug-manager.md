---
title: "偵錯的工作階段管理員 | Microsoft Docs"
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
  - "此工作階段檢視的工作階段偵錯管理員"
  - "工作階段偵錯管理員廣播"
  - "偵錯 [偵錯 SDK]，偵錯的工作階段管理員"
  - "偵錯的工作階段管理員"
  - "工作階段偵錯管理員] 中，偵錯引擎多工作業"
  - "委派的工作階段偵錯管理員"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 偵錯的工作階段管理員
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

工作階段偵錯管理員 \(SDM\) 管理任何偵錯任何數量的程式中任何數目的電腦上的多個處理序的偵錯引擎 \(DE\) 的數目。  除了多工器偵錯引擎，SDM 會提供對 IDE 統一的檢視偵錯工作階段。  
  
## 工作階段偵錯管理員作業  
 工作階段偵錯管理員 \(SDM\) 管理 DE。  可能有一個以上的電腦上執行一次的偵錯引擎。  Multiplex DEs，SDM 會包裝從 DEs 的介面數目與公開這些屬性的 IDE，做為單一的介面。  
  
 多工來提升效能，某些介面不是處理。  相反地，直接從 DE，使用它們，並呼叫這些介面不會通過 SDM。  多工，例如記憶體、 程式碼，與文件內容所使用的介面不是處理，因為它們參考特定的指令、 記憶體或在偵錯特定 DE 特定程式中的文件。  沒有其他 DE 必須涉及在該層級的通訊。  
  
 這不是所有的內容之內，則為 true。  運算式評估內容介面的呼叫會經過 SDM。  運算式評估期間 SDM 會換行[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ，因為該運算式評估時，它可能包含多個正在偵錯程式可能在相同執行緒上執行的處理序的 DEs 提供 IDE 的介面。  
  
 SDM 通常會做為一種委派機制，但它可能扮演廣播的機制。  例如，運算式的評估期間 SDM 扮演廣播的機制，來通知所有 DEs 他們可以在指定的執行緒上執行程式碼。  同樣地，當 SDM 收到停止事件時，它會廣播給他們應該停止執行的所有程式。  呼叫一個步驟時，SDM 廣播到所有的程式就可以繼續執行。  中斷點也會為每個 DE 廣播。  
  
 SDM 不會追蹤目前的程式、 執行緒或堆疊框架。  處理程序、 程式及執行緒資訊傳送到特定的偵錯事件搭配 SDM。  
  
## 請參閱  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)