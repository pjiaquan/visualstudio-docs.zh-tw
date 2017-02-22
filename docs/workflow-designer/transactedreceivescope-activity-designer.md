---
title: "TransactedReceiveScope 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TransactedReceiveScope 活動設計工具
\[**TransactedReceiveScope**\] 設計工具會用來建立及設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動。  
  
## TransactedReceiveScope 活動  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可讓您將交易流動至工作流程或發送器建立的服務端交易。  
  
### 使用 TransactedReceiveScope 活動設計工具  
 \[**TransactedReceiveScope**\] 活動設計工具位於 \[**工具箱**\] 的 \[**傳訊**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 上的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**TransactedReceiveScope**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處。這會建立一個 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，具有 TransactedReceiveScope 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**TransactedReceiveScope**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
 \[**TransactedReceiveScope**\] 設計工具包含 \[**要求**\] 與 \[**本文**\] 方塊。這些會用來設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 屬性，而該屬性會指定 <xref:System.ServiceModel.Activities.Receive> 活動與 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 屬性，而此屬性再指定某個其他 <xref:System.Activities.Activity>。<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 會建立交易。然後，此交易會變成 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 範圍的環境交易，於是此範圍內的任何活動會在此交易的內部執行。  
  
### TransactedReceiveScope 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 屬性，並且描述屬性在設計工具中的使用方式。這些 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯，但其他屬性必須在設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可選用的易記名稱。預設為 TransactedReceiveScope。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|將一個 <xref:System.ServiceModel.Activities.Receive> 活動置入活動設計工具介面上的 \[**要求**\] 區塊。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|將一個 <xref:System.Activities.Activity> 置入活動設計工具介面上的 \[**本文**\] 區塊。|  
  
## 請參閱  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)