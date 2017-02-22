---
title: "ReceiveAndSendReply 樣板設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ReceiveAndSendReply 樣板設計工具
\[**ReceiveAndSendReply**\] 範本會用來在一個 <xref:System.Activities.Statements.Sequence> 活動內建立一對預先設定的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.SendReply> 活動，這些活動相互關聯，屬於伺服器上要求與回應訊息交換模式的一部分。  
  
## ReceiveAndSendReply 範本  
 加入 \[ **ReceiveAndSendReply**\] 範本時，除了以 <xref:System.Activities.Statements.Sequence> 活動建立 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.SendReply> 活動之外，還會進行三項操作：  
  
1.  設定 <xref:System.ServiceModel.Activities.Receive> 活動的 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 與 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 屬性。  
  
2.  將 <xref:System.ServiceModel.Activities.Receive> 活動的 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。  
  
3.  建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。  
  
### 使用 ReceiveAndSendReply 範本設計工具  
 \[**ReceiveAndSendReply**\] 活動設計工具位於 \[**工具箱**\] 的 \[**傳訊**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**ReceiveAndSendReply**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處。這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動 \(可利用 \[**Send**\] 活動設計工具加以設定\) 以及相互關聯的 <xref:System.ServiceModel.Activities.SendReply> \(可利用 \[SendReplyToReceive\] 設計工具加以設定\)。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用 \[**Receive**\] 設計工具設定 <xref:System.ServiceModel.Activities.Receive> 活動的詳細資訊，請參閱[Receive](../workflow-designer/receive-activity-designer.md)主題。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用 \[**SendReplyToReceive**\] 設計工具設定 <xref:System.ServiceModel.Activities.SendReply> 活動的詳細資訊，請參閱下一節。  
  
### SendReply 的屬性  
 下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。預設為 SendReplyToReceive。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|參考到與這個 <xref:System.ServiceModel.Activities.SendReply> 活動成對的 <xref:System.ServiceModel.Activities.Receive> 活動。這個屬性不可為 **null**。伺服器會同時使用 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動，以製作要求\/回應傳訊模式的模型。這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.SendReply> 活動的來源 <xref:System.ServiceModel.Activities.Send> 活動。|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|指定要接收的訊息或參數內容。這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。若要編輯此屬性，請按一下屬性方格中 \[**內容**\] 欄位旁邊的橢圓形按鈕，或是按一下 \[**Receive**\] 活動設計工具介面上 \[**內容**\] 標籤旁邊的 \[**定義**\] 按鈕。兩者都顯示 \[**內容定義**\] 對話方塊。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解如何使用此方塊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。按一下屬性方格中 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 屬性旁邊的省略符號按鈕，以開啟 \[**新增相互關聯初始設定式**\] 對話方塊。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解如何使用此方塊，請參閱[加入相互關聯初始設定式對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|指定訊息的動作標頭。如果沒有明確設定，其值會預設為：<br /><br /> **https:\/\/tempuri.org\/{服務合約命名空間}\/{服務合約名稱}\/{作業名稱}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|指定傳送回覆訊息前是否要保存工作流程服務執行個體。預設值為 **false**。|  
  
## 請參閱  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)