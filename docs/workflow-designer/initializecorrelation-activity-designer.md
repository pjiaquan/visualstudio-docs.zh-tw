---
title: "InitializeCorrelation 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# InitializeCorrelation 活動設計工具
\[**InitializeCorrelation**\] 活動設計工具會用來建立及設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，而該活動是用來在傳送或接受訊息前，先建立訊息之間的相互關聯。  
  
## InitializeCorrelation 活動  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。相互關聯通常會在傳送或接收訊息時初始化。如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。  
  
### 使用 InitializeCorrelation 活動設計工具  
 \[**InitializeCorrelation**\] 活動設計工具位於 \[**工具箱**\] 的 \[**傳訊**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**InitializeCorrelation**\] 活動設計工具可以從 \[**工具箱**\] 拖曳至 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上。這會建立一個 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，具有 InitializeCorrelation 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**InitializeCorrelation**\] 活動設計工具的標頭中編輯，或是在 \[**屬性**\] 視窗的 \[**DisplayName**\] 方塊中編輯。  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> 可以在 \[**InitializeCorrelation**\] 活動設計工具介面上 \[**屬性**\] 視窗的 \[**相互關聯**\] 欄位中指定。  
  
 按一下 \[**屬性**\] 視窗中 \[**CorrelationData**\] 欄位上的省略符號按鈕，或 \[**InitializeCorrelation**\] 活動設計工具介面上的 \[檢視\] 提示文字，就會顯示 \[**InitializeCorrelation**\] 對話方塊，您可從中指定相互關聯控制代碼，以及用來初始化的索引鍵值組。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解如何使用此對話方塊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。  
  
### InitializeCorrelation 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.InitializeCorrelation> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在 \[**屬性**\] 視窗中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。預設值為 InitializeCorrelation。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用 \[**初始化相互關聯**\] 對話方塊可以設定 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解此對話方塊的用法，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。|  
  
## 請參閱  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)