---
title: "PickBranch 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# PickBranch 活動設計工具
<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。  
  
## PickBranch  
 <xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick> 活動的 <xref:System.Activities.Statements.Pick.Branches%2A> 集合中。每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。透過這種方式，[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供了事件架構的控制流程模型。每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
### 如何使用 Pick 活動設計工具  
 \[**PickBranch**\] 設計工具位於 \[**工具箱**\] 的 \[**控制流程**\] 分類中。若要存取它，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 依預設，最初將 \[**Pick**\] 活動設計工具置放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的時候，就會建立兩個空的 <xref:System.Activities.Statements.PickBranch> 物件，顯示名稱為 \[**Branch1**\] 與 \[**Branch2**\]，做為 <xref:System.Activities.Statements.Pick> 活動的項目。各自的 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 屬性值可以在 \[**PickBranch**\] 設計工具的標頭中編輯，或是在各分支的 \[**屬性**\] 視窗內編輯。  
  
 有兩個方法可以將 <xref:System.Activities.Statements.PickBranch> 物件加入至 <xref:System.Activities.Statements.Pick> 物件的集合：一是從 \[**工具箱**\] 拖放 \[**PickBranch**\] 設計工具，二是使用 \[**Pick**\] 設計介面中的內容功能表：  
  
1.  將 \[**PickBranch**\] 設計工具從 \[**工具箱**\] 中拖曳出來，然後放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上的 \[**Pick**\] 活動設計工具其中一個分支時，就會建立一個 <xref:System.Activities.Statements.PickBranch>。新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。以滑鼠將 \[**PickBranch**\] 設計工具拖曳到 \[**Pick**\] 設計工具時，\[**Pick**\] 設計工具會使用垂直的藍灰色帶，指出某個特定滑鼠位置會將 <xref:System.Activities.Statements.PickBranch> 加到哪裡。  
  
2.  以滑鼠右鍵按一下 \[**Pick**\] 活動設計工具 \(但不是在 \[**PickBranch**\] 設計工具內部\)，即可取得內容功能表，再選取 \[**Create Branch**\] 即可新增 <xref:System.Activities.Statements.PickBranch>。請注意，在 \[**Pick**\] 設計工具中，新的 <xref:System.Activities.Statements.PickBranch> 會加到現有 <xref:System.Activities.Statements.PickBranch> 物件的右邊。  
  
 \[**PickBranch**\] 設計工具可以展開，以顯示 \[**觸發程序**\] 與 \[**動作**\] 方塊。若要摺疊，只要按一下各個標題右邊的雙箭頭符號即可。若要編輯各個 <xref:System.Activities.Statements.PickBranch> 的 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 與 <xref:System.Activities.Statements.PickBranch.Action%2A>，請將活動放進其設計工具的 \[**觸發程序**\] 與 \[**動作**\] 方塊。  
  
 在 <xref:System.Activities.Statements.Pick> 物件的 <xref:System.Activities.Statements.Pick.Branches%2A> 集合中，可以重新排列 <xref:System.Activities.Statements.PickBranch> 物件的順序，只要在 \[**Pick**\] 設計工具內，將物件拖放到新的位置即可。\[**Pick**\] 設計工具會使用垂直藍灰色帶，指出某個特定滑鼠位置會將 <xref:System.Activities.Statements.PickBranch> 加到哪裡。  
  
 有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：  
  
1.  選取 \[**PickBranch**\] 設計工具，加以刪除。  
  
2.  選取 \[**PickBranch**\] 設計工具，按滑鼠右鍵取得內容功能表，然後選擇 \[**刪除**\]。  
  
 請確實選取 \[**PickBranch**\] 設計工具，因為若是誤選 \[**觸發程序**\] 或 \[**動作**\] 方塊內的其中一個活動，就會刪除其中的活動，而不會刪除 <xref:System.Activities.Statements.PickBranch> 物件。  
  
### 工作流程設計工具中的 PickBranch 屬性  
 下表顯示最實用的 <xref:System.Activities.Statements.PickBranch> 屬性，並且說明它們在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|顯示在 \[**PickBranch**\] 設計工具標頭中的易記名稱。預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|  
  
## 請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)   
 [選擇活動](../Topic/Pick%20Activity.md)   
 [使用 Pick 活動](../Topic/Using%20the%20Pick%20Activity.md)