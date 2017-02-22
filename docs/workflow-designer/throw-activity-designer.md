---
title: "Throw 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Throw 活動設計工具
\[**Throw**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Throw> 活動。  
  
## Throw 活動  
 <xref:System.Activities.Statements.Throw> 活動會擲回例外狀況。  
  
### 使用 Throw 活動設計工具  
 \[**Throw**\] 活動設計工具位於 \[**工具箱**\] 的 \[**錯誤處理**\] 類別中，按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\) 即可存取。  
  
 \[**Throw**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Throw> 活動，具有 Throw 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**Throw**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。<xref:System.Activities.Statements.Throw.Exception%2A> 屬性必須在屬性方格中編輯。  
  
### 擲回屬性  
 下表顯示 <xref:System.Activities.Statements.Throw> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Throw> 活動選用的易記名稱。預設為 Throw。|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|要擲回的例外狀況。此例外狀況必須衍生自 <xref:System.Exception>。若要指定例外狀況，請在屬性方格中輸入 Visual Basic 運算式。|  
  
## 請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)