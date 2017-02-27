---
title: "ForEach&lt;T&gt; 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ForEach&lt;T&gt; 活動設計工具
<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Values%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Body%2A> 中包含的活動。  
  
## 工作流程設計工具中的 ForEach\<T\> 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|----------|---------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。預設值為 ForEach\<Int32\>。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|要重複項目的集合。若要設定 <xref:System.Activities.Statements.ForEach%601.Values%2A>，請在 \[**ForEach\<T\>**\] 活動設計工具上或在屬性方格的 \[**值**\] 方塊中輸入 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 運算式。|  
|*TypeArgument*|True|泛型參數 *T* 指定的 <xref:System.Activities.Statements.ForEach%601.Values%2A> 集合中項目的型別。依預設，*TypeArgument* 會設為 **Int32**。若要變更型別，請在屬性方格中，變更下拉式方塊內 *TypeArgument* 的值。|  
  
 依預設，迴圈 Iterator 會命名為 **item**。您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。  
  
## 請參閱  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)