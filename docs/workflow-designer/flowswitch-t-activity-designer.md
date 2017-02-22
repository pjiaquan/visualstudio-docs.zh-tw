---
title: "FlowSwitch&lt;T&gt; 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowSwitch&lt;T&gt; 活動設計工具
<xref:System.Activities.Statements.FlowSwitch%601> 活動是條件式節點，當需要兩個以上的替代分支時，該節點會根據相符的準則提供控制流程的分支。如果流程分支僅需要兩個路徑，請改用 <xref:System.Activities.Statements.FlowDecision> 活動。  
  
## FlowSwitch\<T\> 活動  
 經評估後，<xref:System.Activities.Statements.FlowSwitch%601> 活動會包含傳回的型別 *T* \(由泛型參數指定\) 值的 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。活動也包含一組 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，這會指定從這個評估的可能結果到一組 <xref:System.Activities.Statements.FlowNode> 物件的唯一對應。已執行的 <xref:System.Activities.Statements.FlowNode>，其型別 *T* 的物件會符合已評估的 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 值。<xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 案例可 \(選擇性\) 地提供給未取得相符結果的案例。  
  
### 使用 FlowSwitch\<T\> 活動設計工具  
 \[**FlowSwitch\<T\>**\] 活動設計工具位於 \[**工具箱**\] 的 \[**流程圖**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**FlowSwitch\<T\>**\] 活動設計工具可從 \[**工具箱**\] 中拖曳出來，並置放到 \[**Flowchart**\] 活動設計工具內的 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上。使用顯示的 \[**選取型別**\] 視窗來指定評估 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 時所取得的型別 \(藉由其泛型參數，以程式碼來與 <xref:System.Activities.Statements.FlowSwitch%601> 相關聯\)。此程序會在 <xref:System.Activities.Statements.Flowchart> 活動內建立標示為 \[**Switch**\] 的 <xref:System.Activities.Statements.FlowSwitch%601> 活動。按一下顯示提示文字 \[輸入 VB 運算式\] 處，即可在 \[**屬性**\] 視窗的 \[**運算式**\] 方塊中輸入 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。  
  
 將滑鼠移到 \[**FlowSwitch\<T\>**\] 活動設計工具上，形成用來連結 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 以顯示其邊緣的方形控點。拖曳 \[**FlowSwitch\<T\>**\] 活動設計工具和其他活動設計工具到 \[**流程圖**\] 後，其所代表的 <xref:System.Activities.Activity> 物件就已經就緒，可相互連結來指定執行順序。若要建立與 <xref:System.Activities.Statements.FlowSwitch%601> 相關聯的其中一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，請按一下 \[**FlowSwitch\<T\>**\] 周圍的其中一個方形案例控點，並將它拖曳 \(按住滑鼠按鈕\) 到另一個控點，此控點是當滑鼠游標移到目的地活動的設計工具上時，以相似方式顯示的控點。放開滑鼠按鈕，隨即出現從 \[**FlowSwitch\<T\>**\] 到目的地設計工具的箭號，以表示此案例。此案例的預設值會顯示在箭號上，且可在 \[**屬性**\] 視窗的 \[**案例**\] 方塊中加以編輯。  
  
### FlowSwitch\<T\> 屬性  
 下表顯示 <xref:System.Activities.Statements.FlowSwitch%601> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中或在設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|指定已評估的運算式，以判斷要將哪一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 切換到執行路徑。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|指定從評估<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 所取得的可能結果到一組<xref:System.Activities.Statements.FlowNode> 物件的唯一對應。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|指定對應，時機是當 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的評估結果與包含於 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 物件的值不相符時。|  
  
## 請參閱  
 [流程圖](../workflow-designer/flowchart-activity-designers.md)   
 [流程圖](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)