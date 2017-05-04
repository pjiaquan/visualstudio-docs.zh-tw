---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted | Microsoft Docs"
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
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  若您要在部署或撤銷 SharePoint 專案時執行額外的工作，可以處理 Visual Studio 所引發的事件。  如需詳細資訊，請參閱[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
### 若要在部署或撤銷 SharePoint 專案時執行程式碼  
  
1.  建立一個專案項目擴充功能、專案擴充功能或新專案項目類型的定義。  如需詳細資訊，請參閱下列主題：  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  在擴充功能中，存取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。  如需詳細資訊，請參閱 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
3.  處理專案服務的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 事件。  
  
4.  在事件處理常式中，使用 <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> 參數取得目前部署工作階段的相關資訊。  例如，您可以判斷哪一個專案處於目前部署工作階段中，以及是否正在部署或撤銷專案。  
  
 下列程式碼範例示範如何處理專案擴充功能中的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 事件。  當啟動和完成 SharePoint 專案的部署時，此擴充功能會將額外的訊息寫入 \[**輸出**\] 視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  