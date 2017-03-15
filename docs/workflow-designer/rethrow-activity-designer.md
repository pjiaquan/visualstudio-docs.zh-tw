---
title: "Rethrow 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Rethrow 活動設計工具
\[**Rethrow**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Rethrow> 活動。  
  
## Rethrow 活動  
 <xref:System.Activities.Statements.Rethrow> 活動會執行先前已擲回的例外狀況。此活動只能用於 <xref:System.Activities.Statements.TryCatch> 活動中的 <xref:System.Activities.Statements.Catch> 處理常式。  
  
### 使用 ReThrow 活動設計工具  
 \[**Rethrow**\] 活動設計工具位於 \[**工具箱**\] 的 \[**錯誤處理**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**Rethrow**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Rethrow> 活動，具有 Throw 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**Rethrow**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### Rethrow 屬性  
 下表顯示 <xref:System.Activities.Statements.Rethrow> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.ReThrow> 活動選用的易記名稱。預設為 Rethrow。|  
  
## 請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)