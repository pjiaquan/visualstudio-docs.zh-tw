---
title: "Persist 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Persist 活動設計工具
\[**Persist**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Persist> 活動。  
  
## Persist 活動  
 只要情況允許，<xref:System.Activities.Statements.Persist> 活動會將工作流程儲存至磁碟。<xref:System.Activities.Statements.Persist> 活動無法在非持續性的區域中執行，例如在 <xref:System.Activities.Statements.TransactionScope> 活動內。如果在非持續性的範圍內使用 <xref:System.Activities.Statements.Persist> 活動，就會在執行階段擲回例外狀況。  
  
### 使用 Persist 活動設計工具  
 \[**Persist**\] 活動設計工具位於 \[**工具箱**\] 的 \[**執行階段**\] 類別中，若要存取，請按一下 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Persist**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Persist> 活動，具有 Persist 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**Persist**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### Persist 屬性  
 下表顯示 <xref:System.Activities.Statements.Persist> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活動的易記名稱。預設為 Persist。雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
  
## 請參閱  
 [執行階段](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)