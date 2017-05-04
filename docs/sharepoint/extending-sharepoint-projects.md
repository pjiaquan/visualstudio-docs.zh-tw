---
title: "Extending SharePoint Projects | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  如果您要自訂 SharePoint 專案的專案層級功能，可建立專案擴充功能。  例如，您可以加入自訂的專案屬性，或回應使用者在 Visual Studio 中開發 SharePoint 解決方案時引發的專案層級事件。  
  
## 建立專案擴充功能  
 若要擴充專案項目，請組建 Visual Studio 擴充功能組件，以實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。  如需詳細資訊，請參閱[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
 專案擴充功能建立之後，您也可以將下列功能加入至 SharePoint 專案：  
  
-   加入捷徑功能表項目。  功能表項目會在您以滑鼠右鍵按一下節點或選取然後選擇 SHIFT \+ F10 鍵開啟一個 SharePoint 專案節點的捷徑功能表上 \[**方案總管**\] 。  如需詳細資訊，請參閱[How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。  
  
-   加入自訂屬性。  當您在 \[ \[**方案總管**\] 時，中的 SharePoint 專案屬性會出現在 \[**屬性**\] 視窗。  如需詳細資訊，請參閱[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 如需示範如何建立、部署和測試專案擴充功能的逐步解說，請參閱[Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。  
  
## 了解專案擴充功能和專案執行個體之間的關聯性  
 當您建立專案擴充功能時，擴充功能會在任何類型的 SharePoint 專案於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟時載入。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含數個 SharePoint 專案範本，例如清單定義、內容類型和事件接收器。  然而，只有一個 SharePoint 專案型別。  出現在 \[**新增專案**\] 對話方塊中的專案型別只是與一個或多個 SharePoint 專案項目搭配在一起的範本。  因為只有一個 SharePoint 專案型別，所以針對一個專案建立的擴充功能會套用至所有 SharePoint 專案。  例如，您無法建立一個擴充功能只套用至 \[**內容類型**\] 項目。  
  
 若要存取特定專案執行個體，請在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法實作中，處理 *projectService* 參數的其中一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 事件。  例如，若要判斷 SharePoint 專案何時加入至方案，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 事件。  如需詳細資訊，請參閱[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## 請參閱  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  