---
title: "使用工作流程設計工具開發應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Visual Studio 2010 工作流程設計工具 [WFD]"
  - "Visual Studio 2010 工作流程設計工具 [WFD], 概觀"
  - "工作流程設計工具 [WFD]"
  - "工作流程設計工具 [WFD], 概觀"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 使用工作流程設計工具開發應用程式
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 是視覺化設計工具，也是偵錯工具，可用於圖形建構與 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 開發環境下所裝載之 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] 中的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 應用程式之偵錯。它可讓您使用範本與活動設計工具，來撰寫複合工作流程應用程式、活動程式庫或 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 服務。[!INCLUDE[crabout](../test/includes/crabout_md.md)]以進一步了解工作流程，請參閱 [Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md)。  
  
 以下是幾個使這個新版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 與舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 不同的新設計功能：  
  
-   使用 [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] 建立的 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。這會提升活動設計工具的體驗，並改善大型且複雜之工作流程的效能。  
  
-   現在會使用 [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] 來設計自訂活動，以簡化為建立活動設計工具而使用 XAML 和程式設計模型的方式。  
  
-   流程圖活動已實作，因此可使用相似的流程圖模型樣式來視覺化程式的流程。  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 有新的變數設計工具，可讓您宣告工作流程內的變數與設定其範圍，以及將變數繫結至活動。  
  
-   在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中，[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 會提供在 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 工作流程內撰寫 Visual Basic 運算式時的完整 IntelliSense 功能。  
  
-   現在，偵錯體驗已延伸到 XAML，您可在 XAML 工作流程定義中設定中斷點，以及在執行階段步入 XAML 程式碼，提供與使用 Managed 程式碼相似的經驗。  
  
-   相較於舊版，重新裝載 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之外的 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 已大幅簡化，現在只需要幾行程式碼即可完成。  
  
-   新<xref:System.Activities.Statements.Flowchart> 活動及其 [流程圖](../workflow-designer/flowchart-activity-designer.md)可讓您使用熟悉的流程圖模型樣式，來視覺化程式流程。  
  
-   傳訊活動已有所加強，可讓您撰寫完全宣告式 \(無程式碼\) 的 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 服務。  
  
-   \[**加入服務參考**\] 功能可讓您自動產生存取 Web 服務的活動。  
  
## 在本節中  
 [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)  
 示範如何使用內建設計工具來建立新的活動與工作流程專案，以及如何使用設計工具提供的其他工具來處理引數、變數、運算式、匯入和階層連結列巡覽。  
  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)  
 描述活動和範本的分類以及系統提供的設計工具。  
  
 [使用工作流程設計工具偵錯工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 描述如何執行傳統偵錯程序，以及偵錯 XAML 與運算式。  
  
 [Workflow 設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)  
 包含 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供之對話方塊的即時線上說明主題，以及有關設計工具殼層功能、鍵盤快速鍵和錯誤訊息的指引。  
  
 [以 .NET 3.0 或 .NET 3.5 Framework 為目標開發工作流程應用程式](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 包含有關使用以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標之舊版設計工具的指引。  
  
 [設計工具重新裝載 &#91;WF 範例&#93;](../Topic/Designer%20ReHosting.md)  
 這個範例示範如何建立 WPF 配置以包含設計工具。  
  
 [自訂活動設計工具](../Topic/Custom%20Activity%20Designers.md)  
 本章節包含了活動範例，這些範例會使用自訂設計工具以顯示在工作流程設計工具中。