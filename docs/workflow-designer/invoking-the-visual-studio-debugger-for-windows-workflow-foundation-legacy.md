---
title: "叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "偵錯工具, 工作流程"
  - "偵錯工作流程, 啟動偵錯工具"
  - "偵錯, 使用工作流程偵錯工具"
  - "逐步進入命令"
  - "跳離函式命令"
  - "不進入函式命令"
  - "逐步執行"
  - "逐步執行, 命令"
  - "工作流程偵錯工具, 啟動"
  - "工作流程, 偵錯工具"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)
本主題描述如何在舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具來偵錯 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式。當您需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 一般而言，偵錯舊版工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。您可以使用下列方法啟動 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation：  
  
-   選取 \[**偵錯**\] 功能表上的 \[**附加至處理序**\]，從可用的處理序中選取執行中的工作流程執行個體。  
  
-   按下 **F5** 以開始執行工作流程的執行個體，或在叫用中斷點後繼續執行。  
  
## 逐步執行程式碼  
 偵錯工具所支援最常見的偵錯程序之一為逐步執行：就是一次執行一行程式碼。逐步執行程式碼的命令有三個：  
  
-   **逐步執行**：使用 **F11** 逐步執行活動。偵錯工具會逐步執行任何已定義的處理常式。如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。以下活動不支援從設計工具逐步進入程式碼處理常式：**IfElseActivity**、**WhileActivity**、**ConditionedActivityGroup** 或 **ReplicatorActivity**。若要偵錯與這些活動相關聯的處理常式，您必須將明確的中斷點放入程式碼中。  
  
-   **跳離函式**：使用 **Shift\-F11** 逐步跳出活動。逐步跳出活動會將目前活動及其同層級活動執行到完成。接著偵錯工具會在目前活動的父代上中斷。從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。  
  
-   **不進入函式**：使用 **F10** 不進入活動。當不進入複合活動時。偵錯工具會在複合活動的第一個可執行子系上中斷。不進入非複合活動 \(例如，**CodeActivity** 活動\) 時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。  
  
## 附加至處理序  
 若要以附加至處理序的方式偵錯工作流程，請在 \[**附加至處理序**\] 對話方塊的 \[**可使用的處理序**\] 清單方塊中選取可用的處理序。如果 \[**自動: 工作流程程式碼**\] 沒有出現在 \[ **附加至**\] 文字方塊中，則請按一下 \[**選取**\]。在 \[**選取程式碼類型**\] 對話方塊中，按一下 \[**偵錯這些程式碼類型**\]，然後選取 \[**工作流程**\]。接著按一下 \[**確定**\]，再按一下 \[**附加**\]。  
  
## 以 F5 偵錯  
 如果工作流程主應用程式 \(Host Application\) 和工作流程 DLL 位在不同的 Visual Studio 專案中，例如，當您使用工作流程活動程式庫時，您必須將工作流程 DLL 專案設為 Visual Studio 方案的啟始專案，才能使用 **F5** 偵錯工作流程。您也必須在工作流程 DLL 專案的 \[**起始外部程式**\] 屬性中，設定主應用程式的路徑。  
  
 若要在 \[方案總管\] 中設定啟始專案，請以滑鼠右鍵按一下專案名稱，並選取 \[**設定為啟始專案**\]。若要在 \[**起始外部程式**\] 屬性中設定主應用程式的路徑，請在 \[方案總管\] 中按兩下工作流程專案的 \[**屬性**\] 節點，並選取 \[**偵錯**\] 索引標籤。在 \[**起始動作**\] 下，選取 \[**起始外部程式**\]，並輸入裝載您要偵錯之工作流程的 .exe 檔案路徑。  
  
 如果主應用程式設為啟始專案，則只會叫用 Visual Studio 偵錯工具進行偵錯，不會叫用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation。如果使用 Visual Studio 偵錯工具，則只會叫用 C\# 或 Visual Basic 程式碼中斷點，不會叫用工作流程設計工具中設定的中斷點。例如，如果使用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation，則會叫用您在設計工具中的 <xref:System.Workflow.Activities.ParallelActivity> 活動上設定的中斷點，但當您使用 Visual Studio 偵錯工具時不會叫用該中斷點。  
  
## 請參閱  
 [HOW TO：在工作流程中設定中斷點 \(舊版\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)