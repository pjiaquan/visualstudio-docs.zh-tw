---
title: "轉換活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 7
---
# 轉換活動設計工具
<xref:System.Activities.Statements.Transition> 表示兩個狀態之間的轉換。  
  
## 使用 Transition 活動設計工具  
 Transition 活動設計工具允許您設定兩個狀態之間的轉換。  
  
### 工作流程設計工具中的 Transition 屬性  
 下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.Transition> 屬性，並說明如何在設計工具中使用它們。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Transition> 活動設計工具的易記名稱。預設值為 **T1**。這個值可以在這些位置進行編輯：屬性方格、展開的轉換設計工具的標頭，以及展開的轉換設計工具內動作區段的標頭。<xref:System.Activities.Activity.DisplayName%2A> 可用於階層連結巡覽，其顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|如果存在，則指定一個運算式，其必須評估為 **True**，控制項才能傳遞給目的地狀態。這個條件可以在屬性方格和展開的轉換設計工具中編輯。共用轉換中的多個條件是以它們在轉換設計工具中的出現順序接受評估。 **Note:**  請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A>評估為 **False** \(或所有共用觸發轉換的條件皆評估為  **False**\)，則不會發生轉換，且會重新排定該狀態之所有轉換的所有觸發。由於設定條件的方式，在本教學課程中不會發生這種情況 \(我們有針對猜測是否正確的具體行動\)。|  
|**來源**|True|表示此轉換所源自的狀態。按一下來源狀態的名稱，可將設計工具檢視切換到該狀態的展開檢視。當轉換已建立且不能變更時會設定此值。|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|指定其完成會起始轉換的活動。若要設定此活動，從 \[**工具箱**\] 將活動拖放到轉換的 \[**Trigger**\] 區段。|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|指定觸發活動完成時和 <xref:System.Activities.Statements.Transition.Condition%2A> \(如果有的話\) 評估為 **true** 時執行的活動在來源狀態的 <xref:System.Activities.Statements.State.Exit%2A> 活動 \(如果有的話\) 執行之後，轉換到目的狀態時會執行此活動。當轉換設計工具展開時，可以從 \[**工具箱**\] 將活動拖放到轉換的 \[**Action**\] 區段來設定此值。單一轉換可以有多個動作。個別的動作可以展開和收縮，而且當轉換有多個動作時，可以按一下出現在動作上的上下箭號來加以排序。|  
|**目的端**|True|表示轉換完成之後狀態機器轉換到的狀態。這個對應至物件模型中轉換的 <xref:System.Activities.Statements.Transition.To%2A> 屬性。按一下目的狀態的名稱，可將設計工具檢視切換到該狀態的展開檢視。當轉換已建立並可用拖曳箭頭 \(其將轉換連接至設計工具中的目的狀態\) 的方式進行變更時，會設定這個值。|  
  
### 建立轉換  
 轉換可由這些方式建立：從某個狀態將線條拖曳到另一個狀態，或將狀態放到三角形上，當某個狀態被拖曳到另一個狀態上方時會出現此三角形。若要以拖曳的方式來建立轉換,，將滑鼠停留在來源狀態的邊緣，並將線條從源狀態拖曳到目的狀態。若要以放置的方式來建立轉換,，拖曳目的狀態並停留在來源狀態上方，然後放到來源狀態周圍之四個三角形的其中一個。目的狀態可以是拖曳自 \[**工具箱**\] 的新狀態，或是拖曳自工作流程設計工具的現有狀態。  
  
> [!NOTE]
>  狀態機器中的單一狀態可以具有最多 76 個以工作流程設計工具建立的轉換。在設計工具外建立的工作流程狀態轉換，其數目上限僅受系統資源限制。  
  
 共用觸發轉換是一組共用相同觸發事件的轉換。共用觸發程序允許對目的狀態的條件式進展，根據的是運算式的評估結果，此運算式是針對多個共用通用觸發事件的轉換所設定。若要將其他動作加入到轉換並建立共用轉換，按一下表示目的狀態的開頭的圓形，然後拖曳到想要的狀態。新的轉換會和初始轉換共用同一個觸發程序，但具有唯一的條件和動作。共用轉換可以從轉換設計工具內建立，方式是按一下轉換設計工具底部的 \[**加入共用觸發轉換**\]，然後從 \[**可連接的狀態**\] 下拉式清單選取想要的目標狀態。  
  
## 請參閱  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [狀態](../workflow-designer/state-activity-designer.md)