---
title: "CancellationScope 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CancellationScope 活動設計工具
\[**CancellationScope**\] 設計工具會用來建立及設定 <xref:System.Activities.Statements.CancellationScope> 活動。  
  
## CancellationScope 活動  
 <xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。  
  
### 使用 CancellationScope 活動設計工具  
 \[**CancellationScope**\] 活動設計工具位於 \[**工具箱**\] 的 \[**交易**\] 分類中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**CancellationScope**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.CancellationScope> 活動，具有 CancellationScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**CancellationScope**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### CancellationScope 屬性  
 下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。<xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。預設為 CancellationScope。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定提供取消邏輯的活動。若要加入 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活動，請從 \[**工具箱**\] 中拖曳出一個活動，放進 \[**CancellationScope**\] 活動設計工具的 \[**本文**\] 方塊，加上提示文字「在此置放活動」。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定如果取消時所要執行的活動。若要加入 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動，請從 \[**工具箱**\] 中拖曳出一個活動，放進 \[**CancellationScope**\] 活動設計工具的 \[**CancellationHandler**\] 方塊，加上提示文字「在此置放活動」。|  
  
## 請參閱  
 [異動](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)