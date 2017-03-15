---
title: "TransactionScope 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionScope 活動設計工具
\[**TransactionScope**\] 設計工具會用來建立及設定 <xref:System.Activities.Statements.TransactionScope> 活動。  
  
## TransactionScope 活動  
 <xref:System.Activities.Statements.TransactionScope> 活動會以單一交易的方式執行其中包含的活動。在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動及交易中所有其他參與者均順利完成之後，就會認可交易。  
  
### 使用 TransactionScope 活動設計工具  
 \[**TransactionScope**\] 活動設計工具位於 \[**工具箱**\] 的 \[**交易**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**TransactionScope**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.TransactionScope> 活動，具有 TransactionScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**TransactionScope**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### TransactionScope 屬性  
 下表顯示 <xref:System.Activities.Statements.TransactionScope> 屬性，並且描述屬性在設計工具中的使用方式。<xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Statements.TransactionScope.Body%2A> 屬性可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。但其他屬性必須在屬性方格上進行編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 活動可選用的易記名稱。預設為 TransactionScope。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|指定要在單一交易中執行的活動。若要加入 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動，請從 \[**工具箱**\] 中拖曳出一個活動，放進 \[**TransactionScope**\] 活動設計工具的 \[**本文**\] 方塊，並加上提示文字「在此置放活動」。|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|為這個 <xref:System.Activities.Statements.TransactionScope> 指定 <xref:System.Transactions.IsolationLevel>。|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|指定交易必須完成的時間間隔 \(格式為 00:00:00，表示時:分:秒\)。預設值是 1 分鐘 \(00:01:00\)。|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|指定值，這個值會指出當交易中止時，工作流程是否應隨之中止。|  
  
## 請參閱  
 [異動](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)