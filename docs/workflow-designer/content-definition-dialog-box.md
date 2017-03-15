---
title: "內容定義對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 內容定義對話方塊
\[**內容定義**\] 對話方塊在 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中用來設定 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的 **Content** 屬性。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解使用此方塊的活動設計工具，請參閱[Send](../workflow-designer/send-activity-designer.md)、 [Receive](../workflow-designer/receive-activity-designer.md)、[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)和 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主題。  
  
 下表說明 \[**初始化相互關聯**\] 對話方塊中的使用者介面 \(UI\) 項目。  
  
|UI 項目|說明|  
|-----------|--------|  
|**訊息**|使用 \[**訊息資料**\] 運算式文字方塊指定訊息內容，並且使用 \[**訊息型別**\] 下拉式清單方塊指定其型別。依預設，\[**內容定義**\] 會使用 <xref:System.ServiceModel.Activities.ReceiveMessageContent>，而這會預期工作流程服務定義範圍內的 <xref:System.ServiceModel.Channels.Message> 或訊息合約型別。|  
|**參數**|按一下 \[**參數**\] 選項按鈕以使用 <xref:System.ServiceModel.Activities.ReceiveParametersContent>，這會預期某個資料合約。使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵\/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|  
  
 \[**內容定義**\] 對話方塊會由 \[**Send**\]、\[**Receive**\]、\[**ReceiveAndSendReply**\] 及 \[**SendAndReceiveReply**\] 設計工具使用。各種情況的存取方式很類似，在此使用 \[Receive\] 為例，以說明這個程序。  
  
 \[**Receive**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處。這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。選取 \[**Receive**\] 活動設計工具，然後按一下屬性方格中 \[**內容**\] 屬性的 \(內容\) 文字旁邊的省略符號按鈕，就會出現 \[**內容定義**\] 對話方塊。  
  
 內容可以在 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動的 \[**訊息**\] 區段內指定，或是在 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動的 \[**參數**\] 區段內指定。  
  
## 請參閱  
 [Workflow 設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)