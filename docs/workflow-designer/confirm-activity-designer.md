---
title: "Confirm 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Confirm.UI"
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Confirm 活動設計工具
\[**Confirm**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Confirm> 活動。  
  
## Confirm 活動  
 <xref:System.Activities.Statements.Confirm> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity> 中之活動的 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>。如果 <xref:System.Activities.Statements.Confirm> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity> 之 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性。  
  
 由 <xref:System.Activities.Statements.Compensate.Target%2A> 指定的 <xref:System.Activities.Statements.CompensationToken> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。  
  
### 使用 Confirm 活動設計工具  
 \[**Confirm**\] 活動設計工具位於 \[**工具箱**\] 的 \[**交易**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Confirm**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Confirm> 活動，具有 Confirm 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**Confirm**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### Confirm 屬性  
 下表顯示 <xref:System.Activities.Statements.Confirm> 屬性，並且描述屬性在設計工具中的使用方式。<xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯，但 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性必須在屬性方格中編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.CancellationScope> 活動選用的易記名稱。預設為 Confirm。|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.Confirm> 活動的 <xref:System.Activities.Statements.CompensationToken>。|  
  
## 請參閱  
 [異動](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)