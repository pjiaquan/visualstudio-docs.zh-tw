---
title: "Extending the SharePoint Project System"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  使用一組專案範本和項目範本在 Visual Studio 中，您可以建立 SharePoint 方案。  這些範本符合許多開發案例的需求，不過，您可能會發現它們並未提供您需要的一些情況。  在這些情況下，您可以擴充 SharePoint 專案系統。  
  
## SharePoint 專案系統概觀  
 SharePoint 專案系統以「*SharePoint 專案項目*」\(SharePoint Poject Item\) 的基本元件為基礎。  SharePoint 專案項目代表單一的 SharePoint 自訂，例如清單定義、Web 組件或內容類型。  
  
 SharePoint 專案是包含一個或多個 SharePoint 專案項目的 Visual Studio 專案。  SharePoint 專案也包含其他元件，這些元件會定義專案項目如何組成「功能」或封裝以供開發之用。  
  
 如需 SharePoint 專案項目及 SharePoint 專案之內容的詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## 如何擴充 SharePoint 專案系統  
 您可以透過下列方式擴充 SharePoint 專案系統：  
  
-   定義自己的 SharePoint 專案項目型別，並且在 Visual Studio 中將這些型別與新的項目範本或專案範本產生關聯。  例如，您可以定義用以建立自訂動作或欄位的 SharePoint 專案項目型別。  如需詳細資訊，請參閱[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
-   擴充已安裝於 Visual Studio 中的 SharePoint 專案項目型別。  例如，在中，當開發人員選取功能表項目時，您可以將捷徑功能表項目加入至 \[**方案總管**\] 的專案項目和自訂專案項目。  如需詳細資訊，請參閱[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。  
  
-   擴充 SharePoint 專案。  例如，在 SharePoint 專案中加入或移除項目時，您可以加入事件處理常式來執行特定工作。  如需詳細資訊，請參閱[Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)。  
  
-   擴充 SharePoint 專案項目及 SharePoint 專案的封裝和部署行為。  例如，您可以建立在部署或撤銷專案時要執行的專屬部署步驟，或是在 Visual Studio 執行特定部署步驟時，執行其他自訂工作。  如需詳細資訊，請參閱[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。  
  
## 一般開發工作  
 您可以在 SharePoint 專案系統的擴充功能中執行下列一般工作：  
  
-   儲存專案項目的自訂字串資料，並以不同類型的專案檔儲存。  如需詳細資訊，請參閱[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
-   將 SharePoint 專案系統中的物件轉換成 Visual Studio Automation 物件模型或整合物件模型中的對應物件，反之亦然。  如需詳細資訊，請參閱[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
## 請參閱  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  