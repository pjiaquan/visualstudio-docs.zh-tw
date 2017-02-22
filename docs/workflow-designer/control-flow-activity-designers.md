---
title: "控制流程活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 控制流程活動設計工具
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 包括幾項系統提供的活動，在您建構工作流程時，可以使用這些活動。本節包含用來控制工作流程中之流程的系統提供活動。下列主題說明會這些活動，並且提供如何使用的指引。  
  
## 在本節中  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 執行其主體包含的活動至少一次，直到指定的條件評估為 **true** 為止。  
  
 [ForEach\<T\>](http://msdn.microsoft.com/zh-tw/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 針對指定集合中的各個項目，執行其主體包含的活動。  
  
 [If](../workflow-designer/if-activity-designer.md)  
 評估條件，並且根據該評估的結果執行某個活動。  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 同時執行屬於同一集合的子活動。  
  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)  
 列舉集合項目，並針對集合的每個項目平行執行內嵌陳述式。  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 根據某個事件提供以事件為主的流程控制，執行若干分支的其中一個做為回應。  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 提供在 <xref:System.Activities.Statements.Pick> 活動內執行的潛在路徑。  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 包含子活動的有序集合，該集合會依序執行。  
  
 [Switch\<T\>](http://msdn.microsoft.com/zh-tw/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 評估指定的運算式，並且根據關聯索引鍵符合求值結果的多個活動，從這些活動的集合中執行該活動。  
  
 [While](../workflow-designer/while-activity-designer.md)  
 在指定之條件評估為 **true** 的同時，執行其主體包含的活動。  
  
## 參考  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## 相關章節  
 如需其他型別之活動設計工具的資訊，請參閱下列主題。  
  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)  
  
 [流程圖](../workflow-designer/flowchart-activity-designers.md)  
  
 [傳訊](../workflow-designer/messaging-activity-designers.md)  
  
 [執行階段](../workflow-designer/runtime-activity-designers.md)  
  
 [基本](../workflow-designer/primitives-activity-designers.md)  
  
 [異動](../workflow-designer/transaction-activity-designers.md)  
  
 [集合](../workflow-designer/collection-activity-designers.md)  
  
 [錯誤處理](../workflow-designer/error-handling-activity-designers.md)  
  
## 外部資源  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)