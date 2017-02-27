---
title: "WriteLine 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# WriteLine 活動設計工具
\[**WriteLine**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.WriteLine> 活動。  
  
## WriteLine 活動。  
 <xref:System.Activities.Statements.Writeline> 活動會將文字寫入至指定的 <xref:System.IO.TextWriter> 物件。如果未指定任何 <xref:System.IO.TextWriter>，<xref:System.Activities.Statements.Writeline> 就會將文字寫入至主控台。  
  
### 使用 WriteLine 活動設計工具  
 \[**WriteLine**\] 活動設計工具位於 \[**工具箱**\] 的 \[**基本**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**WriteLine**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.WriteLine> 活動，具有 WriteLine 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**WriteLine**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### WriteLine 屬性  
 下表顯示 <xref:System.Activities.Statements.WriteLine> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 活動的易記名稱。預設值為 WriteLine。雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|要寫入的文字。若要設定此屬性，請在 \[**WriteLine**\] 活動設計工具上的 \[**文字**\] 方塊或在屬性方格中輸入 Visual Basic 運算式。|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.Activities.Statements.WriteLine> 從中寫入 <xref:System.Activities.Statements.WriteLine.Text%2A> 的 <xref:System.IO.TextWriter>。預設值為主控台。|  
  
## 請參閱  
 [基本](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)