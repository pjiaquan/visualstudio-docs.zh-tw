---
title: "Delay 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Delay.UI"
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Delay 活動設計工具
\[**Delay**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Delay> 活動。  
  
## Delay 活動  
 <xref:System.Activities.Statements.Delay> 活動會延遲某個工作流程的執行，等候指定的時間長度。  
  
### 使用 Delay 活動設計工具  
 \[**Delay**\] 活動設計工具位於 \[**工具箱**\] 的 \[**基本**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Delay**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Delay> 活動，具有 Delay 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**Delay**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### Delay 屬性  
 下表顯示 <xref:System.Activities.Statements.Delay> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|----------|---------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> 活動的易記名稱。預設為 Delay。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|延遲工作流程的時間長度。這個屬性會在屬性方格中設定。輸入常值 <xref:System.TimeSpan> \(使用 00:00:00 格式\) 或 Visual Basic 運算式，即可指定時間長度。|  
  
## 請參閱  
 [基本](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay Activity Designer](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)