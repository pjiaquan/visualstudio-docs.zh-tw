---
title: "If 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# If 活動設計工具
<xref:System.Activities.Statements.If> 活動會評估條件，並且根據該評估的結果執行某個活動。這個活動最適合用於使用程式設計的程序模型樣式時。例如，<xref:System.Activities.Statements.If> 活動可巢狀置入 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Parallel> 活動內部。如果您要使用 <xref:System.Activities.Statements.Flowchart> 活動，可以考慮改用 <xref:System.Activities.Statements.FlowDecision> 活動。  
  
## 工作流程設計工具中的 If 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.If> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|判斷要執行哪個子活動的條件。若要設定 <xref:System.Activities.Statements.If.Condition%2A>，請在 \[**If**\] 活動設計工具上或在屬性方格的 \[**條件**\] 方塊中輸入 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式。|  
|<xref:System.Activities.Statements.If.Else%2A>|False|如果 <xref:System.Activities.Statements.If.Condition%2A> 是 **false** 時所要執行的活動。若要加入由 <xref:System.Activities.Statements.If.Else%2A> 分支執行的活動，請從 \[**工具箱**\] 中拖曳出一個活動，放進 \[**If**\] 活動設計工具上的 \[**Else**\] 方塊，並加上提示文字「在此置放活動」。|  
|<xref:System.Activities.Statements.If.Then%2A>|False|如果 <xref:System.Activities.Statements.If.Condition%2A> 是 **true** 時所要執行的活動。若要加入由 <xref:System.Activities.Statements.If.Then%2A> 分支執行的活動，請從 \[**工具箱**\] 中拖曳出一個活動，放進 \[**If**\] 活動設計工具上的 \[**Then**\] 方塊，並加上提示文字「在此置放活動」。|  
  
## 請參閱  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)