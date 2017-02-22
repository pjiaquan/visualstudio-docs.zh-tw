---
title: "從遠端電腦偵錯工作流程 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "偵錯工作流程, 遠端"
  - "偵錯, 遠端"
  - "遠端偵錯, 工作流程"
  - "工作流程, 遠端偵錯"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 從遠端電腦偵錯工作流程 (舊版)
本主題描述如何偵錯使用舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 所建置的遠端舊版 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式。當您的應用程式需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 當您安裝 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 時，其中一個元件安裝選項可用來安裝 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]。這會安裝遠端偵錯元件。這些遠端偵錯元件必須安裝在要進行遠端工作流程偵錯的目標電腦上。  
  
 此外，包含您在遠端電腦上所偵錯之舊版工作流程之工作流程定義的組件，必須安裝在進行偵錯的來源本機電腦的全域組件快取 \(GAC\) 中。例如，如果舊版工作流程是在遠端電腦 A 上執行，而您要從本機電腦 B 偵錯該工作流程，則工作流程定義必須位於電腦 B 的 GAC 中。如此可讓設計工具將執行於遠端電腦 A 之工作流程的工作流程標記，在電腦 B 上還原序列化並加以顯示。如需全域組件快取的詳細資訊，請參閱 MSDN Library。  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 遠端偵錯的運作方式與其他 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 元件的遠端偵錯功能相同。如需詳細資訊，請參閱 MSDN Library 中的＜[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 遠端偵錯＞。  
  
## 請參閱  
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)