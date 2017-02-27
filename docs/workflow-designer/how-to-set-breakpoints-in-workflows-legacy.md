---
title: "HOW TO：在工作流程中設定中斷點 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "中斷點, 在工作流程中設定"
  - "偵錯工作流程, 設定中斷點"
  - "偵錯, 在工作流程中設定中斷點"
  - "工作流程, 設定中斷點"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# HOW TO：在工作流程中設定中斷點 (舊版)
本主題描述如何在使用舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 建置的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式中設定中斷點。當您的 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 應用程式需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 當您在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 來建置 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 應用程式時，您可以在 C\# 和 Visual Basic 程式碼中設定中斷點，就像在 Visual Studio 中一樣。如預期般，工作流程執行會在您設定的每個中斷點上停止。  
  
 中斷點有三種狀態：「*擱置*」\(Pending\)、「*繫結*」\(Bound\) 和「*錯誤*」\(Error\)。設定中斷點時，狀態為「擱置」，由空心的紅色圖示表示。執行階段已載入工作流程類型時，中斷點會變成「繫結」狀態，由實心的紅色圖示表示。如果您指定錯誤的中斷點格式，且活動名稱無效，則會顯示錯誤視窗。中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。  
  
 在工作流程設計介面中，您可以使用以下方式在活動中設定中斷點：  
  
-   以滑鼠右鍵按一下活動並選取 \[**中斷點 \\ 插入中斷點**\]。  
  
-   選取該活動並按 F9。  
  
-   從 \[**偵錯**\] 功能表中選取 \[**新增中斷點**\]。  
  
     當偵錯工具在中斷點處停止時，您也可以使用這個選項來設定偵錯時的新中斷點。  
  
    > [!NOTE]
    >  不支援在已叫用的工作流程上設定中斷點。  
  
### 若要使用偵錯功能表上的新增中斷點選項設定中斷點  
  
1.  從 \[**偵錯**\] 功能表上，選取 \[**新增中斷點**\]。  
  
2.  按一下 \[**在函式中斷**\]。  
  
     \[**新增中斷點**\] 對話方塊隨即開啟。  
  
3.  使用以下語法，在 \[**函式**\] 文字方塊中指定活動的名稱：`QualifiedActivityId[:[FullClassName][:InstanceId]]`。  
  
    > [!NOTE]
    >  您可以選擇以指定工作流程活動絕對路徑的方式設定中斷點，而不要使用 \[**函式**\] 文字方塊中的活動名稱。例如，假設您有一個名為 **WorkflowConsoleApplication1** 的工作流程解決方案，其中有一個名為 **Workflow1** 的工作流程，這個工作流程使用名為 **Delay1** 的活動。您可以使用 **Delay1** 活動名稱，或指定以下的路徑：**Delay1:WorkflowConsoleApplication1.Workflow1** 或 **Delay1:WorkflowConsoleApplication1.Workflow1:{6614886A\-608E\-412B\-BF98\-99FF1559DDDF}**。  
  
4.  選取 \[**使用 IntelliSense**\] 核取方塊來驗證函式名稱。  
  
     如果未選取這個核取方塊，則不會執行中斷點名稱驗證。  
  
5.  選取 \[ **語言**\] 清單中的 \[**工作流程**\]。  
  
6.  按一下 \[**確定**\]。  
  
## 請參閱  
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)   
 [叫用 Visual Studio Debugger for Windows Workflow Foundation \(舊版\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)