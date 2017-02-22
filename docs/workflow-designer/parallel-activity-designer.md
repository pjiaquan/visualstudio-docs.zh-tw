---
title: "Parallel 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Parallel 活動設計工具
<xref:System.Activities.Statements.Parallel> 活動會並行執行屬於同一集合的子活動。  
  
## Parallel 活動  
 <xref:System.Activities.Statements.Parallel> 活動會將它的子活動儲存在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。如果某些子活動可能閒置，請使用 <xref:System.Activities.Statements.Parallel> 活動，而不是 <xref:System.Activities.Statements.Sequence> 活動。  
  
 <xref:System.Activities.Statements.Parallel> 活動有一個 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 屬性，其中包含使用者指定的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式。在各個分支完成之後，<xref:System.Activities.Statements.Parallel> 活動會評估這個屬性。如果評估為 **True**，則 <xref:System.Activities.Statements.Parallel> 活動會完成，不會執行其他分支。如果 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 不會評估為 **True**，則 <xref:System.Activities.Statements.Parallel> 活動會在所有子活動都已完成時才完成。  
  
### 使用 Parallel 活動設計工具  
 \[**Parallel**\] 活動設計工具位於 \[**工具箱**\] 的 \[**控制流程**\] 分類中。若要存取它，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Parallel**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動設計工具的任一處，例如在某個 \[**Sequence**\] 活動設計工具內部。放進 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 之後，就會建立 <xref:System.Activities.Statements.Parallel> 活動，此活動預設包含 **Parallel** 的 <xref:System.Activities.Activity.DisplayName%2A>。  
  
 若要將活動加入至 Parallel 活動的 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中，請從 \[**工具箱**\] 將一些其他活動設計工具拖曳至 \[**Parallel**\] 活動設計工具內的三角形上。三角形與分支內包含的活動相接。可以重複這個程序來加入其他活動。您可以在 \[**Parallel**\] 活動設計工具內拖放活動來重新排列。  
  
### 工作流程設計工具中的 Parallel 活動屬性  
 下表顯示 Parallel 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。預設值為 **Parallel**。此值可在 \[**屬性**\] 方格中編輯，或是直接在活動設計工具標頭上編輯。|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要執行之子活動的集合。|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成後評估。如果評估為 **True**，則會取消已排程的擱置中分支。如果這個屬性未設定或是評估為 **False**，則活動會在所有子活動都已完成時才完成。預設值為 **null**。|  
  
## 請參閱  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)