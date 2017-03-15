---
title: "ClearCollection&lt;T&gt; 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ClearCollection&lt;T&gt; 活動設計工具
\[**ClearCollection\<T\>**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.ClearCollection%601> 活動。  
  
## ClearCollection\<T\> 活動  
 <xref:System.Activities.Statements.ClearCollection%601> 活動會清除所有項目的指定集合。  
  
### 使用 ClearCollection\<T\> 活動設計工具  
 \[**ClearCollection\<T\>**\] 活動設計工具位於 \[**工具箱**\] 的 \[**集合**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**ClearCollection\<T\>**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.ClearCollection%601> 活動，具有 ClearCollection\<Int32\> 的預設 <xref:System.Activities.Activity.DisplayName%2A>\(預設的 *TypeArgument* 是 **Int32**。這可以在屬性方格中變更\)。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**ClearCollection\<T\>**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。其他的屬性必須在屬性方格上進行編輯。  
  
### ClearCollection\<T\> 屬性  
 下表顯示 <xref:System.Activities.Statements.ClearCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.ClearCollection%601> 活動選用的易記名稱。預設為 ClearCollection\<Int32\>。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|指定要清除項目的集合。此集合屬於 **ICollection\<TypeArgument\>.** 型別。若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|  
|*TypeArgument*|True|指定 <xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。根據預設，這個 *TypeArgument* 型別會設定為 **Int32**。若要變更型別，請在屬性方格中，變更下拉式方塊中 *TypeArgument* 的值。|  
  
## 請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)