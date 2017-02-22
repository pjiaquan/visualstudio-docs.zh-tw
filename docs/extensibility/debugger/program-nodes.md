---
title: "程式節點 | Microsoft Docs"
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
  - "程式節點，偵錯內容"
  - "偵錯 [偵錯 SDK]，程式節點"
  - "程式節點加入"
  - "取代的程式節點"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 程式節點
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯工具的架構的角度來看**程式節點**：  
  
-   是輕量型程式的說明。  
  
-   可以識別本身以及它正在執行中，並可以附加至中斷連結，並說明如果有的話，請建立它時，偵錯引擎 \(DE\) 的程序。  
  
-   由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面，通常由 DE 或連接埠。  程式節點時，會加入至連接埠上，藉由呼叫[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。  當程式節點加入至連接埠時，會將它加入至包含此程式\] 節點代表的程式處理序。  
  
 有時要啟動偵錯工作階段，根據偵錯套件中，實作後程式節點用來建立對應程式中。  當查詢處理程序時，它的程式時，列舉程式，另一個則用於程式中的每一個節點。  
  
 程式附加到之前，IDE 就會需要該程式的輕量級描述。  這項資訊可以取自 \[程式\] 節點。  一旦程式附加到，IDE 就需要顯示更詳細的資訊，例如在程式中執行的所有執行緒的清單。  這項資訊被取自程式本身。  
  
## 請參閱  
 [Programs](../../extensibility/debugger/programs.md)   
 [處理序](../../extensibility/debugger/processes.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)