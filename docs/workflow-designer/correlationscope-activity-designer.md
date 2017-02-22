---
title: "CorrelationScope 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CorrelationScope 活動設計工具
\[**CorrelationScope**\] 活動設計工具會用來建立及設定 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，該活動會使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件提供子系傳訊活動的隱含管理。  
  
## CorrelationScope 活動  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。包含在 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 中的 <xref:System.ServiceModel.Activities.Send> 與 <xref:System.ServiceModel.Activities.Receive> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性來執行相互關聯。  
  
### 使用 CorrelationScope 活動設計工具  
 \[**CorrelationScope**\] 活動設計工具位於 \[**工具箱**\] 的 \[**傳訊**\] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 左側的 \[**工具箱**\] 索引標籤 \(也可以從 \[**檢視**\] 功能表選取 \[**工具列**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**CorrelationScope**\] 活動設計工具可以從 \[**工具箱**\] 拖曳至 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上。這會建立一個 <xref:System.ServiceModel.Activities.CorrelationScope> 活動，具有 CorrelationScope 的預設 \[**DisplayName**\]。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**CorrelationScope**\] 活動設計工具的標頭中編輯，或是在 \[**屬性**\] 視窗的 \[**DisplayName**\] 方塊中編輯。  
  
 若要指定子系傳訊活動使用的 <xref:System.ServiceModel.Activities.CorrelationHandle>，請按一下 \[**屬性**\] 視窗的 \[**CorrelatesWith**\] 欄位旁邊的橢圓形按鈕，以顯示 \[**運算式編輯器**\] 對話方塊。這個屬性也可以在活動設計工具介面上設定。  
  
 若要指定相互關聯範圍內的活動，請將其設計工具置放在 \[**CorrelationScope**\] 設計工具內的 \[**本文**\] 方塊內。  
  
### CorrelationScope 屬性  
 下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可在 \[**屬性**\] 視窗中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯，通常兩者都可以。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動可選用的易記名稱。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。如果沒有設定這個屬性，<xref:System.ServiceModel.Activities.CorrelationScope> 會自動建立隱含 <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定相互關聯範圍內的活動。|  
  
## 請參閱  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)