---
title: "How to: Execute a SharePoint Command"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  如果您要在 SharePoint 工具擴充功能中使用伺服器物件模型，則必須建立自訂的「*SharePoint 命令*」\(SharePoint Command\) 來呼叫 API。  在定義命令並使用 SharePoint 工具擴充功能部署該命令之後，擴充功能會執行該命令，以呼叫 SharePoint 伺服器物件模型。  若要執行命令，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件的其中一個 ExecuteCommand 方法。  
  
 如需 SharePoint 命令用途的詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### 若要執行 SharePoint 命令  
  
1.  在 SharePoint 工具擴充功能中，取得 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件。  取得 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件的方式根據建立的擴充功能類型而定：  
  
    -   在 SharePoint 專案系統的擴充功能中，使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> 屬性。  
  
         如需專案系統擴充功能的詳細資訊，請參閱[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
    -   在 \[**伺服器總管**\] 的 \[**SharePoint 連接**\] 節點擴充功能中，使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> 屬性。  若要取得 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> 物件，請使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> 屬性。  
  
         如需 \[**伺服器總管**\] 擴充功能的詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
    -   在不屬於 SharePoint 工具擴充功能的程式碼中 \(例如專案範本精靈\)，使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 屬性。  
  
         如需擷取專案服務的詳細資訊，請參閱[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件的其中一個 ExecuteCommand 方法。  將您要執行的命令名稱傳遞至 ExecuteCommand 方法的第一個引數。  如果命令具有自訂參數，請將該參數傳遞至 ExecuteCommand 方法的第二個引數。  
  
     每一個支援的命令簽章都有不同的 ExecuteCommand 多載。  下表列出支援的簽章和每一個簽章使用的多載。  
  
    |命令簽章|要使用的 ExecuteCommand 多載|  
    |----------|----------------------------|  
    |命令只有預設的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數，沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令只有預設的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數和傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令有兩個參數 \(預設的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數和自訂參數\)，沒有傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |命令有兩個參數和一個傳回值。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## 範例  
 下列程式碼範例示範了如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 多載呼叫在 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)中所述的 `Contoso.Commands.UpgradeSolution` 命令。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 在此範例中顯示的 `Execute` 方法是 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> 方法的實作，其屬於自訂部署步驟中的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 介面。  若要在完整的範例內容中查看這個程式碼，請參閱[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
 請注意下面關於 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 方法之呼叫的詳細資料：  
  
-   第一個參數會識別您要呼叫的命令。  此字串與您傳遞至命令定義上 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 的值相符。  
  
-   第二個參數是您要傳遞至命令的第二個自訂參數的值。  在此情況下，它是要更新至 SharePoint 網站之 .wsp 檔案的完整路徑。  
  
-   程式碼並未傳遞隱含的 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數至命令。  當您從 SharePoint 專案系統的擴充功能，或是 \[**伺服器總管**\] 中 \[**SharePoint 連接**\] 節點的擴充功能呼叫命令時，該參數便會自動傳遞至命令。  在其他類型的方案中 \(例如，實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的專案範本精靈\)，此參數為 **null**。  
  
## 編譯程式碼  
 這個範例需要參考 Microsoft.VisualStudio.SharePoint 組件。  
  
## 請參閱  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  