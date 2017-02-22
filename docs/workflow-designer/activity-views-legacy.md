---
title: "活動檢視 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "活動, 活動檢視"
  - "活動檢視"
  - "檢視, 活動"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 活動檢視 (舊版)
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 提供的許多活動 \(工作流程組成的元素\) 具有舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中所提供的幾個設計檢視。當您將 \[**工具箱**\] 中的活動設計工具拖曳至設計介面後，之後每次選取活動時，便可以使用 \[**工作流程**\] 功能表或以滑鼠右鍵按一下選取的活動，在不同的設計檢視間切換。此外，當您將指標移至選取活動的名稱上方時，會顯示一組下拉式索引標籤，可用來在不同的檢視之間切換。  
  
 每個活動至少會有一個檢視，這是當您將 \[**工具箱**\] 中的活動設計工具拖曳至設計介面上時顯示的預設檢視。這個活動的預設檢視在功能表和索引標籤上以 \[**檢視 \[活動類型\]**\] 選項的方式提供，例如 \[**檢視 Parallel**\]。大部分的活動會有額外的檢視，不同的活動可以有不同的檢視。例如，[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) \(英文\) 活動有補償檢視，[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) \(英文\) 活動有事件檢視。許多 Windows Workflow Foundation 隨附的活動有 \[**檢視取消處理常式**\] 和 \[**檢視錯誤**\] 設計檢視，可檢視與這些活動相關聯的 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) \(英文\) 和 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) \(英文\)。  
  
 下表列出每個檢視的名稱和說明。  
  
|功能表\/索引標籤選項|說明|  
|-----------------|--------|  
|**檢視 \[活動類型\]**|選取此功能表或索引標籤選項可檢視所選活動的預設圖形表示。|  
|**檢視取消處理常式**|選取此功能表或索引標籤選項可檢視與所選活動相關聯的 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) \(英文\)。|  
|**檢視錯誤處理常式**|選取此功能表或索引標籤選項可檢視與所選活動相關聯的 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) \(英文\)。|  
|**檢視補償處理常式**|選取此功能表或索引標籤選項可檢視與所選 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) \(英文\) 相關聯的 [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) \(英文\)。|  
|**檢視事件處理常式**|選取此功能表或索引標籤選項可檢視與所選 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) \(英文\) 相關聯的 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) \(英文\)。|  
  
 如需類似檢視的資訊，請參閱[循序工作流程檢視 \(舊版\)](../workflow-designer/sequential-workflow-views-legacy.md)。  
  
## 請參閱  
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [循序工作流程檢視 \(舊版\)](../workflow-designer/sequential-workflow-views-legacy.md)