---
title: "Assign 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Assign 活動設計工具
\[**Assign**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Assign> 活動。  
  
## Assign 活動  
 <xref:System.Activities.Statements.Assign> 活動會指派值給變數或引數。  
  
### 使用 Assign 活動設計工具  
 \[**Assign**\] 活動設計工具位於 \[**工具箱**\] 的 \[**基本**\] 類別中，若要存取，請按一下 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Assign**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上活動通常放置的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Assign> 活動，具有 Assign 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**Assign**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### Assign 屬性  
 下表顯示 <xref:System.Activities.Statements.Assign> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> 活動的易記名稱。預設為 Assign。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> 指派至的變數或引數。這必須是有效的 Visual Basic 識別項。若要設定此屬性，請在 \[**Assign**\] 活動設計工具上的 \[**至**\] 方塊或在屬性方格中輸入 Visual Basic 運算式。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|指派給變數的值。若要設定 <xref:System.Activities.Statements.Assign.Value%2A>，請在 \[**Assign**\] 活動設計工具上的 \[**值**\] 方塊或在屬性方格中輸入 Visual Basic 運算式。|  
  
## 請參閱  
 [基本](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)