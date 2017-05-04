---
title: "How to: Run Code When Deployment Steps are Executed | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Run Code When Deployment Steps are Executed
  如果您要針對 SharePoint 專案中某個部署步驟執行額外的工作，可以在 Visual Studio 執行每一個部署步驟前後處理 SharePoint 專案項目所引發的事件。  如需詳細資訊，請參閱[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 若要在執行部署步驟時執行程式碼  
  
1.  建立一個專案項目擴充功能、專案擴充功能或新專案項目類型的定義。  如需詳細資訊，請參閱下列主題：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在擴充功能中，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 物件 \(在專案項目擴充功能或專案擴充功能中\) 或 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件 \(在新專案項目類型的定義中\) 的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 事件。  
  
3.  在事件處理常式中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 和 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 參數取得有關部署步驟的資訊。  例如，您可以判斷哪一個部署步驟正在執行，以及正在部署或撤銷方案。  
  
## 範例  
 下列程式碼範例示範如何處理 \[清單執行個體\] 專案項目擴充功能中的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 事件。  若 Visual Studio 於部署和撤銷方案時重複使用應用程式集區，此擴充功能就會將額外的訊息寫入 \[**輸出**\] 視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handledeploymentstepevents.cs#4)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handledeploymentstepevents.vb#4)]  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  