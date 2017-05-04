---
title: "匯入可重複使用之工作流程的方針 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "匯入項目 [Visual Studio 中的 SharePoint 開發]"
  - "可重複使用的工作流程 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 匯入項目"
  - "Visual Studio 中的 SharePoint 開發, 可重複使用的工作流程"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 匯入可重複使用之工作流程的方針
  若要匯入以 SharePoint Designer 建立的可重複使用工作流程，請在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中使用 \[匯入可重複使用的 SharePoint 2010 工作流程\] 專案範本。  這個範本會匯入「*宣告式**工作流程*」\(Declarative Workflow\) \(僅限 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\)，並將其轉換成可以使用 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 程式碼強化的「*程式碼工作流程*」\(Code Workflow\)。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 但 \[匯入可重複使用的 SharePoint 2010 工作流程\] 範本只能匯入陣列方案。  如果您要部署工作流程做為沙箱化方案，請使用 \[匯入 SharePoint 2010 方案套件\] 範本匯入。  但採用這種方式將無法將其轉換成程式碼工作流程，因而無法加以修改。  
  
## 使用匯入可重複使用的工作流程範本來匯入可重複使用的工作流程  
 如果您使用 \[匯入可重複使用的 SharePoint 2010 工作流程\] 範本匯入可重複使用的工作流程，您可以像對任何其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 方案一樣執行或變更方案，但您必須手動修正某些項目。  
  
### 匯入工作表單  
 \[匯入可重複使用的 SharePoint 2010 工作流程\] 專案範本會匯入所有的初始表單和關聯表單，但只會匯入一份工作表單，這是因為程式碼工作流程結構描述僅允許一份工作表單。  所有其他來自原始工作流程方案的工作表單，都會放置在 \[**方案總管**\] 的 \[**其他匯入的檔案**\] 資料夾中。  
  
## 使用匯入 SharePoint 2010 方案套件範本，來匯入可重複使用的工作流程  
 如果您要使用 \[匯入 SharePoint 2010 方案套件\] 範本匯入可重複使用的工作流程，您必須考慮下列問題：  
  
-   匯入工作流程後，只要按 F5 鍵，即可立即在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中部署和執行。  但如果您在匯入的方案中變更工作流程中的任何項目，則可能必須先手動修正專案中的項目，才能部署和執行工作流程。  
  
-   由於此工作流程式是宣告式的，因此無法在其中加入程式碼。  若要將工作流程轉換成程式碼工作流程，您必須使用 \[匯入可重複使用的 SharePoint 2010 工作流程\] 範本，將其匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  
  
-   雖然您可以在 \[設計\] 檢視中編輯工作流程設計工具 \(.xoml\) 檔案，但建議您還是在 \[原始碼\] 檢視中進行編輯，因為工作流程設計工具會顯示誤報的錯誤。  
  
-   工作流程中的偵錯並不適用於宣告式內容。  並不會叫用 [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] 中設定的中斷點。  
  
## 匯入可全域重複使用的工作流程方案  
 您無法透過 \[匯入可重複使用的 SharePoint 2010 工作流程\] 範本來匯入可全域重複使用的工作流程。  若要匯入可全域重複使用的工作流程，您必須將其轉換成無法全域重複使用的工作流程，或必須使用 \[匯入 SharePoint 2010 方案套件\] 範本。  
  
 若要轉換工作流程，請在 SharePoint Designer 中建立可全域重複使用工作流程的複本 \(開啟工作流程的功能捷徑表然後選擇 \[**另存複本**\]\)。  接著請使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 \[匯入可重複使用的 SharePoint 2010 工作流程\] 範本，匯入可重複使用的新工作流程。  
  
 若要以原狀匯入可全域重複使用的工作流程，請使用 \[匯入 SharePoint 2010 方案套件\] 範本。  若您使用此方法，工作流程並不會轉換成程式碼工作流程，而會保持為宣告式工作流程。  
  
## 請參閱  
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  