---
title: "Interop 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Interop 活動設計工具
\[**Interop**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Interop> 活動。  
  
## Interop 活動  
 <xref:System.Activities.Statements.Interop> 活動會管理工作流程內 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> 所衍生型別的執行。  
  
### 使用 Interop 活動設計工具  
 \[**Interop**\] 活動設計工具位於 \[**工具箱**\] 的 \[**移轉**\] 類別中，若要存取，請按一下 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 如果您的專案是針對完整的 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]，則包含 <xref:System.Activities.Statements.Interop> 活動的[移轉](../workflow-designer/migration-activity-designers.md)類別只會在 \[**工具箱**\] 中出現。  
  
 對於 C\# 專案，您可以重新擬定專案目標，使用完整的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]，其方法是在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，並選取 \[**屬性**\]。在 \[**應用程式**\] 索引標籤上，選取 \[**目標 Framework**\] 中的 \[**.NET Framework 4**\] 選項。顯示 \[**目標 Framework 變更**\] 對話以詢問您是否確認變更時，請選取對話方塊中的 \[**是**\] 按鈕。  
  
 對於 VB 專案，您可以重新擬定專案目標，使用完整的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]，其方法是在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，並選取 \[**屬性**\]。按一下 \[**編譯**\] 索引標籤上的 \[**進階編譯選項**\] 按鈕。選取 \[**目標 Framework**\] 清單中的 \[**.Net Framework 4**\]，然後按一下 \[**確定**\]。顯示 \[**目標 Framework 變更**\] 對話以詢問您是否確認變更時，請選取對話方塊中的 \[**是**\] 按鈕。  
  
 \[**Interop**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.Interop> 活動，具有 Interop 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**Interop**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
 在 \[**Interop**\] 活動設計工具上或在屬性方格中，按一下 \[**ActivityType**\] 方塊中的 \[**按一下以瀏覽**\] 文字，即可叫出 \[**瀏覽並選取 .Net 型別**\] 對話方塊。此時只會顯示工作流程 3.0 或工作流程 3.5 活動 \(亦即只有衍生自 <xref:System.Workflow.ComponentModel.Activity> 的型別\)。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解如何使用此方塊來指定型別，請參閱[瀏覽並選取 .NET 類型對話方塊](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)主題。  
  
### Interop 屬性  
 下表顯示 <xref:System.Activities.Statements.Interop> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 活動的易記名稱。預設為 Interop。雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|指定 <xref:System.Activities.Statements.Interop> 活動所包含之活動的活動型別。指定的型別必須衍生自 <xref:System.Workflow.ComponentModel.Activity>。|  
  
## 請參閱  
 [移轉](../workflow-designer/migration-activity-designers.md)