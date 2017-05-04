---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  在某些情況下，您可能在 SharePoint 專案系統中擁有物件，但是想要使用 Visual Studio Automation 物件模型或整合物件模型中對應物件的功能，反之亦然。  在這些情況下，您可以使用 SharePoint 專案服務的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，來將物件轉化為不同的物件模型。  
  
 例如，您可能有 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件，但是想要使用只在 <xref:EnvDTE.Project> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 物件上提供的方法。  在此情況下，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 轉換成 <xref:EnvDTE.Project> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>。  
  
 如需 Visual Studio 自動化物件模型和 Visual Studio 整合物件模型的詳細資訊，請參閱[Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## 轉換的類型  
 下表列出此方法可以在 SharePoint 專案系統和其他 Visual Studio 物件模型之間轉換的類型。  
  
|SharePoint 專案系統類型|Automation 和整合物件模型中對應的類型|  
|-----------------------|------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 或<br /><br /> 專案的基礎 COM 物件所實作之 Visual Studio 整合物件模型中的任何介面。  這些類別和介面包括 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(或衍生介面\) 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  如需專案所實作之主要介面的清單，請參閱[專案模型的核心元件](../extensibility/internals/project-model-core-components.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 或<br /><br /> <xref:System.UInt32> 值 \(也稱為 VSITEMID\)，這個值會識別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 中包含其本身的專案成員。  這個值可以傳遞至某些 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法的 *itemid* 參數。|  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法，將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件轉換成 <xref:EnvDTE.Project>。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 這個範例需要：  
  
-   SharePoint 專案系統的擴充功能，其具有 EnvDTE.dll 組件的參考。  如需詳細資訊，請參閱[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   程式碼，會註冊 `projectService_ProjectAdded` 方法以處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 事件。  如需範例，請參閱 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## 請參閱  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  