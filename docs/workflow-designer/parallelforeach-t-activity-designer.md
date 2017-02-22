---
title: "ParallelForEach&lt;T&gt; 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ParallelForEach&lt;T&gt; 活動設計工具
<xref:System.Activities.Statements.ParallelForEach%601> 活動會列舉集合的項目，並且平行執行集合中各個項目的內嵌陳述式，而這是同一個執行緒上的非同步處理。如果預期此活動的子活動會進入閒置狀態，請使用這個流量控制活動代替 <xref:System.Activities.Statements.Sequence> 活動。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> 活動有一個 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 屬性，其中包含使用者指定的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式。在各個分支完成之後，<xref:System.Activities.Statements.ParallelForEach%601> 活動會評估這個屬性。如果評估為 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會完成，不會執行其他分支。如果 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 評估不是 **true**，則 <xref:System.Activities.Statements.ParallelForEach%601> 活動會在所有子活動都已完成時才完成。  
  
## ParallelForEach\<T\> 活動  
 <xref:System.Activities.Statements.ParallelForEach%601> 會列舉其值，並且為列舉的每一個值排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。只會排程 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>。主體執行的方式取決於 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 是否變成閒置。  
  
 如果 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 沒有變成閒置，就會依相反順序執行，因為排程的活動會做為一個堆疊處理，所以最後排程的活動會最先執行。例如，如果您在 <xref:System.Activities.Statements.ParallelForEach%601> 中有 {1,2,3,4} 集合，並且使用 **WriteLine** 做為主體將值寫出。主控台會有 4, 3, 2, 1 列印出來。這是因為 **WriteLine** 沒有變成閒置，所以在排程 4 **WriteLine** 活動之後，就會使用堆疊行為來執行 \(先進後出\)。  
  
 但是，如果您在 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 中有活動可以變成閒置，像是 <xref:System.ServiceModel.Activities.Receive> 活動或 <xref:System.Activities.Statements.Delay> 活動。那麼，則不需要等候這些完成。<xref:System.Activities.Statements.ParallelForEach%601> 會移至下一個排程的主體活動，且會嘗試執行此活動。如果該活動也變成閒置，<xref:System.Activities.Statements.ParallelForEach%601> 就會再移至下一個主體活動。  
  
### 使用 ParallelForEach\<T\> 活動設計工具  
 \[**ParallelForEach\<T\>**\] 活動設計工具位於 \[**工具箱**\] 的 \[**控制流程**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**ParallelForEach\<T\>**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如在某個 \[**序列**\] 活動設計工具內部。放進 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 之後，就會建立 <xref:System.Activities.Statements.ParallelForEach%601> 活動，此活動預設包含 **ParallelForEach\<Int32\>.** 的<xref:System.Activities.Activity.DisplayName%2A>。  
  
### 工作流程設計工具中的 ParallelForEach\<T\> 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.ParallelForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。預設值為 **ParallelForEach\<Int32\>**。此值可在 \[**屬性**\] 方格中編輯，或是直接在活動設計工具標頭上編輯。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|集合中每個項目要執行的活動。若要加入 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> 活動，請從工具箱拖出一個活動，放進 \[**ParallelForEach\<T\>**\] 活動設計工具的 \[**本文**\] 方塊，加上提示文字「在此置放活動」。|  
|**TypeArgument**|True|泛型參數 *T* 指定的 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> 集合中項目的型別。依預設，**TypeArgument** 會設為 **Int32**。若要變更 \[**ParallelForEach\<T\>**\] 活動設計工具中的型別 T，請變更屬性方格中 \[**TypeArgument**\] 下拉式方塊的值。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|要重複項目的集合。若要設定 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>，請在有「輸入 VB 運算式」提示文字的方塊中，於 \[**ForEach\<T\>**\] 活動設計工具上的 \[**值**\] 方塊中輸入 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式，或是在 \[**屬性**\] 視窗中的 \[**值**\] 方塊內輸入。|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||在每個反覆運算完成之後評估。如果評估為 true，則會取消已排程的擱置中反覆運算。如果並未設定此屬性，則會執行所有已排程的陳述式，直到完成為止。|  
  
 依預設，迴圈 Iterator 會命名為 item。您可以在 \[**ParallelForEach\<T\>**\] 活動設計工具的 \[**ForEach**\] 方塊中變更 Iterator 變數的名稱。迴圈 Iterator 可用在 <xref:System.Activities.Statements.ParallelForEach%601> 活動子系中的運算式。  
  
## 請參閱  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)