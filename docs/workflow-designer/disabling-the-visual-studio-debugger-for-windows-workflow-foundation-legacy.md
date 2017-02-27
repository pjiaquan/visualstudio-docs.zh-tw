---
title: "停用 Visual Studio Debugger for Windows Workflow Foundation (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "偵錯工作流程, 停用偵錯工具"
  - "工作流程偵錯工具, 停用"
  - "工作流程, 停用偵錯工具"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 停用 Visual Studio Debugger for Windows Workflow Foundation (舊版)
本主題描述在舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中建置 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式時，如何透過組態檔停用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具。當您需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 根據預設，將會針對主機處理序啟用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]。若要停用工作流程偵錯，您必須將 "DisableWorkflowDebugging" 項目加入至主機組態檔中 **\<system.diagnostics\>** 區段的 **\<switches\>** 項目內來明確關閉偵錯。  
  
 下列範例示範如何修改主機組態檔來停用工作流程偵錯。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 [叫用 Visual Studio Debugger for Windows Workflow Foundation \(舊版\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)