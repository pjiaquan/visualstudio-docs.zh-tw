---
title: "FlowDecision 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowDecision 活動設計工具
<xref:System.Activities.Statements.FlowDecision> 節點是條件式節點，會根據是否滿足指定條件來提供控制流程的二選一分支。如果流程要求兩個以上的分支，請改用 <xref:System.Activities.Statements.FlowSwitch%601>。  
  
## FlowDecision 節點  
 當流程可分支為兩個路徑時，請使用 <xref:System.Activities.Statements.FlowDecision>。<xref:System.Activities.Statements.FlowDecision> 節點有 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 以及與以下兩種可能結果之一相關聯的 <xref:System.Activities.Statements.FlowNode>：<xref:System.Activities.Statements.FlowDecision.True%2A> 或 <xref:System.Activities.Statements.FlowDecision.False%2A>。<xref:System.Activities.Statements.FlowDecision.Condition%2A> 會加以評估，且此評估的值會判斷在 <xref:System.Activities.Statements.Flowchart> 內要處理的下一個 <xref:System.Activities.Statements.FlowNode>。  
  
### 使用 FlowDecision 設計工具  
 \[**FlowDecision**\] 設計工具位於 \[**工具箱**\] 的 \[**流程圖**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**FlowDecision**\] 設計工具可從 \[**工具箱**\] 中拖曳出來，並置放到 \[**Flowchart**\] 活動設計工具內的 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上。這會建立在 <xref:System.Activities.Statements.Flowchart> 活動內建立標示為 \[**Decision**\] 的 <xref:System.Activities.Statements.FlowDecision>。將滑鼠游標移到設計工具和 \[**True**\] 與 \[**False**\] 方形控點，即會出現兩個分支。  
  
 拖曳 \[**FlowDecision**\] 設計工具和其他設計工具到 \[**流程圖**\] 後，節點就可相互連結來指定執行順序。若要建立來源節點間的連結 \(包含 \[**FlowDecision**\] 的 \[**True**\] 和 \[**False**\] 分支\) 與目的地節點，將滑鼠游標移到來源節點的設計工具，方形控點就會顯示於每一邊上。按一下方形控點，按住滑鼠按鈕加以拖曳到目的地節點中的另一個控點，此控點是當滑鼠游標移到目的地活動的設計工具上時，以相似方式顯示的控點。放開滑鼠按鈕，這兩個節點之間就會建立連結，此連結會以箭號表示，從來源設計工具指向目的地設計工具。  
  
 按一下顯示提示文字 \[輸入 VB 運算式\] 處，即可在 \[**屬性**\] 視窗的 \[**運算式**\] 方塊中輸入表示 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的運算式。  
  
### FlowDecision 屬性  
 下表顯示 <xref:System.Activities.Statements.FlowDecision> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中或在設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|判斷流程控制要採取的條件限制。|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|如果滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|如果不滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|  
  
## 請參閱  
 [流程圖](../workflow-designer/flowchart-activity-designers.md)   
 [流程圖](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)