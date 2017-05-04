---
title: "How to: Handle Deployment Conflicts | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  您可以自行提供程式碼，處理 SharePoint 專案項目的部署衝突。  例如，您可以判斷部署位置是否已有目前專案項目中的任何檔案，然後在部署目前專案項目之前先刪除已部署的檔案。  如需部署衝突的詳細資訊，請參閱[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 若要處理部署衝突  
  
1.  建立一個專案項目擴充功能、專案擴充功能或新專案項目類型的定義。  如需詳細資訊，請參閱下列主題：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在擴充功能中，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 物件 \(在專案項目擴充功能或專案擴充功能中\) 或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件 \(在新專案項目類型的定義中\) 的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件。  
  
3.  在事件處理常式中，根據案例所套用的準則，判斷正在部署的專案項目與 SharePoint 網站上已部署的方案之間是否有衝突。  您可以使用事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> 屬性來分析正在部署的專案項目，而且可以呼叫為此目的定義的 SharePoint 命令來分析位於部署位置的檔案。  
  
     針對許多衝突類型，您可能要先判斷正在執行的部署步驟。  您可以使用事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> 屬性進行判斷。  雖然在進行內建 <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> 部署步驟期間偵測衝突完全合乎情理，但您還是可以在進行任何部署步驟期間檢查是否有衝突。  
  
4.  如果有衝突，請使用事件引數之 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 屬性的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 方法，建立新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 物件，  這個物件表示有部署衝突。  在 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 方法的呼叫中，也請指定被呼叫用來解決衝突的方法。  
  
## 範例  
 下列程式碼範例會示範處理專案項目擴充功能中清單定義專案項目之部署衝突的基本程序。  若要處理不同專案項目類型的部署衝突，請將不同字串傳遞到 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。  如需詳細資訊，請參閱[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
 為求簡化，這個範例中的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件處理常式假設部署衝突存在 \(亦即，它永遠會加入新的 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 物件\)，而 `Resolve` 方法只會傳回 **true** 表示已解決衝突。  在真實的案例中，<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 事件處理常式會先判斷目前專案項目中的檔案與位於部署位置的檔案之間是否有衝突，然後只會在有衝突的情況下加入 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 物件。  例如，您可以使用事件處理常式中的 `e.ProjectItem.Files` 屬性來分析專案項目中的檔案，而且可以呼叫 SharePoint 命令來分析位於部署位置的檔案。  同樣地，在真實的案例中，`Resolve` 方法可以呼叫 SharePoint 命令來解決 SharePoint 網站上的衝突。  如需建立 SharePoint 命令的詳細資訊，請參閱 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  