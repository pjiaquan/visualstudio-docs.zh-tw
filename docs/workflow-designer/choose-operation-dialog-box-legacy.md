---
title: "選擇作業對話方塊 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 選擇作業對話方塊 (舊版)
本主題描述如何在舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中使用 \[**選擇作業**\] 對話方塊。當您需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 \[**選擇作業**\] 對話方塊可用來選取要與 <xref:System.Workflow.Activities.ReceiveActivity> 活動或 <xref:System.Workflow.Activities.SendActivity> 活動產生關聯的作業。如需搭配使用這個對話方塊與那些活動的詳細資訊，請參閱 [HOW TO：實作 WCF 合約作業 \(舊版\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 和 [HOW TO：叫用 WCF 合約作業 \(舊版\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)。  
  
 下表描述 \[**選擇作業**\] 對話方塊中的使用者介面 \(UI\) 項目。  
  
|UI 項目|說明|  
|-----------|--------|  
|**新增 合約**|為您建立新合約。您可以在這個合約上定義新作業。\(這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用\)|  
|**新增 作業**|將新作業加入至您在 \[**選擇作業**\] 對話方塊中建立的新合約。 **Note:**  您只能將新作業加入至透過 \[**選擇作業**\] 對話方塊建立的合約。 <br /><br /> \(這個介面僅能與 <xref:System.Workflow.Activities.ReceiveActivity> 搭配使用\)|  
|**匯入**|匯入先前定義的合約，並允許您從該合約選取作業。|  
|**作業 名稱**|目前選取之作業的名稱。只有在您已透過 \[**選擇作業**\] 對話方塊建立作業時，才能使用這個文字方塊進行編輯。|  
|**參數**|索引標籤，包含目前所選取作業的參數定義。 **Note:**  只有在您已透過 \[**選擇作業**\] 對話方塊建立作業時，才能變更參數定義。|  
|**屬性**|索引標籤，包含用於用戶端和服務之間所傳送之訊息的 <xref:System.Net.Security.ProtectionLevel> 設定。 **Note:**  只有在您已透過 \[**選擇作業**\] 對話方塊建立作業時，才能啟用這個索引標籤。|  
|**權限**|索引標籤，包含允許呼叫該作業之使用者的 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 和 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 屬性。例如，如果只允許來自 Administrators 群組的使用者呼叫該作業，請在 \[**角色**\] 文字方塊中寫入 "Administrators"。<br /><br /> 這個索引標籤會為透過 \[**選擇作業**\] 對話方塊建立的作業，以及透過 \[**匯入**\] 按鈕匯入的作業而啟用。|  
  
> [!NOTE]
>  \[**選擇作業**\] 對話方塊只會顯示工作流程中其他 <xref:System.Workflow.Activities.SendActivity> 活動所使用的合約或作業。同樣地，<xref:System.Workflow.Activities.ReceiveActivity> 活動的 \[**選擇作業**\] 對話方塊只會顯示工作流程中其他 **ReceiveActivity** 活動所使用的合約或作業。  
  
## 請參閱  
 [HOW TO：實作 WCF 合約作業 \(舊版\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [HOW TO：叫用 WCF 合約作業 \(舊版\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [舊版 Windows Workflow Foundation UI 設計工具的說明](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)