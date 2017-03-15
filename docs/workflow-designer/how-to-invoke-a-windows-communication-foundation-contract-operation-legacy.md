---
title: "HOW TO：叫用 Windows Communication Foundation 合約作業 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# HOW TO：叫用 Windows Communication Foundation 合約作業 (舊版)
本主題描述當使用以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標的舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 時，如何叫用 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 合約作業。  
  
 將工具箱中的 \[**SendActivity**\] 活動拖曳至工作流程設計介面之後，您必須匯入現有的合約，並判斷將從該 \[**SendActivity**\] 活動叫用哪個作業。請透過[選擇作業對話方塊 \(舊版\)](../workflow-designer/choose-operation-dialog-box-legacy.md)選取您的合約及其作業。  
  
 此外，如果您正在使用組態檔搭配您的服務，則必須指定 <xref:System.Workflow.Activities.ChannelToken>。<xref:System.Workflow.Activities.ChannelToken> 會識別您的傳送活動將用於連線至工作流程服務的端點組態。  
  
### 若要從 SendActivity 活動叫用 WCF 合約作業  
  
1.  在設計工具中按兩下 \[**SendActivity**\] 活動，或在 \[**屬性**\] 窗格中按一下 \[**ServiceOperationInfo**\] 屬性旁邊的省略符號。  
  
2.  當 \[**選擇作業**\] 對話方塊開啟時，按一下對話方塊右上角的 \[**匯入**\]。  
  
     [瀏覽並選取 .NET 類型對話方塊 \(舊版\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)隨即開啟。  
  
3.  搜尋含有您所要之合約的組件或專案。  
  
4.  選取合約，然後按一下 \[**確定**\]。  
  
5.  在 \[**可用的作業**\] 下，選取您要叫用的作業，然後按一下 \[**確定**\]。  
  
### 若要指定通道權杖  
  
1.  選取設計工具中的 <xref:System.Workflow.Activities.SendActivity> 活動。  
  
2.  在 \[**屬性**\] 窗格中，為 <xref:System.Workflow.Activities.ChannelToken> 指定名稱。這個名稱會唯一識別通道權杖。  
  
3.  展開通道權杖節點，然後為將在 <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> 欄位使用的用戶端端點指定名稱。組態檔中相同名稱的端點組態將用於設定通道。  
  
4.  如果端點組態已不存在，請在組態檔中建立端點組態。如需設定用戶端的詳細資訊，請參閱 [WCF 用戶端概觀](../Topic/WCF%20Client%20Overview.md)。  
  
## 請參閱  
 [選擇作業對話方塊 \(舊版\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [HOW TO：實作 WCF 合約作業 \(舊版\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)