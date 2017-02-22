---
title: "While 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# While 活動設計工具
在指定的 <xref:System.Activities.Statements.Condition%2A> 評估為 **true** 的同時，<xref:System.Activities.Statements.While> 活動會執行其 <xref:System.Activities.Statements.While.Body%2A> 中包含的活動。包含的活動可能永遠不會執行。如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。  
  
## 工作流程設計工具中的 While 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。預設值為 While。此值可在 \[**屬性**\] 視窗中編輯，或直接在活動設計工具標頭上進行編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.While.Body%2A>|False|包含在 <xref:System.Activities.Statements.Condition%2A> 評估為 **true** 的時所要執行的活動。|  
|<xref:System.Activities.Statements.Condition%2A>|True|包含要評估的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式，用於判斷是否要執行 <xref:System.Activities.Statements.While.Body%2A> 中的活動。|  
  
## 請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)