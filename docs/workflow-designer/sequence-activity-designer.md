---
title: "Sequence 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Sequence 活動設計工具
<xref:System.Activities.Statements.Sequence> 活動會包含子活動的已排序集合，而該集合會依序執行。  
  
 另一種依序執行一組活動的方式，則是使用 <xref:System.Activities.Statements.Flowchart> 活動。當您有簡易的分支或迴圈執行的程式，又考慮以動態方式建立模型時，請考慮使用 [流程圖](../workflow-designer/flowchart-activity-designer.md)。  
  
## 使用 Sequence 活動設計工具  
 若要新增 <xref:System.Activities.Statements.Sequence> 活動，請從 \[**工具箱**\] 將 \[**Sequence**\] 活動設計工具拖曳至 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 介面上。若要新增子活動到這個 <xref:System.Activities.Statements.Sequence> 活動，請從 \[**工具箱**\] 將一些其他活動拖曳至出現提示文字「在此置放活動」的三角形上。  
  
### 工作流程設計工具中的 Sequence 活動屬性  
 下表顯示 <xref:System.Activities.Statements.Sequence> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中或在設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Sequence> 活動設計工具在標頭中的易記名稱。預設值為 Sequence。此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
  
## 請參閱  
 [流程圖](../workflow-designer/flowchart-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)