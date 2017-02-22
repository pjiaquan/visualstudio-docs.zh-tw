---
title: "AddToCollection&lt;T&gt; 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.AddToCollection`1.UI"
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# AddToCollection&lt;T&gt; 活動設計工具
\[**AddToCollection\<T\>**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.AddToCollection%601> 活動。  
  
## AddToCollection\<T\> 活動  
 <xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。  
  
### 使用 AddToCollection\<T\> 活動設計工具  
 \[**AddToCollection\<T\>**\] 活動設計工具位於 \[**工具箱**\] 的 \[**集合**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**AddToCollection\<T\>**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.AddToCollection%601> 活動，具有 AddToCollection\<Int32\> 的預設 <xref:System.Activities.Activity.DisplayName%2A>\(預設的 *TypeArgument* 是 **Int32**。這可以在屬性方格中變更\)。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**AddToCollection\<T\>**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。其他的屬性必須在屬性方格上進行編輯。  
  
### AddToCollection\<T\> 屬性  
 下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。預設為 AddToCollection\<Int32\>。雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要加入至 Collection\<T\> 的項目。此項目屬於 *T* 型別，而該型別則屬於 *TypeArgument* 型別。若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|應該加入項目的集合。這個集合屬於 **ICollection\<TypeArgument\>** 型別。若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。根據預設，這個 *TypeArgument* 型別會設定為 **Int32**。若要變更型別，請在屬性方格中，變更下拉式方塊中 *TypeArgument* 的值。|  
  
## 請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)