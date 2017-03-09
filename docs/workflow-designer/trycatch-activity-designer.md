---
title: "TryCatch 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TryCatch 活動設計工具
\[**TryCatch**\] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.TryCatch> 活動。  
  
## TryCatch 活動  
 <xref:System.Activities.Statements.TryCatch> 活動包含 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動，是 **Catch\<TException\>** 和 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動的集合。型別 **TException** 的 <xref:System.Activities.Statements.Catch%601> 包含 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> 和 <xref:System.Activities.Statements.Catch%601.Action%2A>。它們會共同用來實作一般例外狀況式錯誤處理機制。<xref:System.Activities.Statements.TryCatch> 活動會嘗試執行其 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動。如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動擲回例外狀況，則 <xref:System.Activities.Statements.TryCatch> 活動會使用其 **Catch\<TException\>** 集合以符合例外狀況。如果有符合的項目，則會執行對應 **Catch\<TException\>** 的 <xref:System.Activities.Statements.Catch%601.Action%2A> 做為例外狀況的錯誤處理邏輯。如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中的活動順利完成，或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 中的活動順利完成，則 <xref:System.Activities.Statements.TryCatch> 活動會執行它的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 活動。[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][例外狀況](../Topic/Exceptions.md).  
  
### 使用 TryCatch 活動設計工具  
 \[**TryCatch**\] 活動設計工具位於 \[**工具箱**\] 的 \[**錯誤處理**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**TryCatch**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，置放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.TryCatch> 活動，具有 TryCatch 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 值可以在 \[**TryCatch**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。其他屬性必須在 \[**TryCatch**\] 活動設計工具的介面上進行編輯。  
  
 按一下 \[**TryCatch**\] 設計工具右上角的展開按鈕，以在展開檢視中查看 \[**Try**\]、\[**Catches**\] 和 \[**Finally**\] 方塊。若要加入 Catch，請按一下 \[**TryCatch**\] 設計工具上的 \[**加入新 Catch**\] 按鈕。按鈕會變更為型別下拉式方塊。請選取例外狀況型別，並按 ENTER 鍵來加入 Catch。加入 **Catch** 後，Catch 區域會展開，且可將活動置放於 Catch 以定義 Catch 的執行邏輯。請注意，展開的 Catch 區域右側有一個文字方塊您可以使用這個文字方塊來命名例外狀況變數。例外狀況變數僅可用於相同 **Catch** 內的活動。  
  
 \[**TryCatch** \] 設計工具不支援編輯 **Catch**。如果您想變更例外狀況型別，必須刪除 **Catch** 並加入新的 Catch。您可以選取 **Catch**，或以滑鼠按一下右鍵存取內容功能表上面的 \[**刪除**\] 功能表加以刪除。  
  
### TryCatch 屬性  
 下表顯示 <xref:System.Activities.Statements.TryCatch> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.TryCatch> 活動選用的易記名稱。預設為 TryCatch。|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|當 <xref:System.Activities.Statements.TryCatch> 執行時，首先執行的活動。|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 活動擲回例外狀況時，要檢查的 **Catch** 項目集合。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|當 <xref:System.Activities.Statements.TryCatch.Try%2A> 和 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中的任何必要活動完成執行時，要執行的活動。<br /><br /> 您必須至少在 <xref:System.Activities.Statements.TryCatch.Catches%2A> 或 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中加入一個活動。|  
  
## 請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)