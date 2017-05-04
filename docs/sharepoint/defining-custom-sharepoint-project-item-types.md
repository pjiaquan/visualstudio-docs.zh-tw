---
title: "Defining Custom SharePoint Project Item Types | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  如果您要建立一種新的 SharePoint 專案項目，請定義新的 SharePoint 專案項目類型。  例如， Visual Studio 不包含 SharePoint 加入的欄位或自訂動作\] 專案項目加入至 SharePoint 網站。  您可以定義自己的 SharePoint 專案項目型別，用以建立欄位、自訂動作或其他類型的 SharePoint 元件。  
  
## 定義 SharePoint 專案項目類型的工作  
 若要定義自訂專案項目類型，請組建 Visual Studio 擴充功能組件，以實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面。  如需詳細資訊，請參閱[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
 當您定義自訂專案項目類型時，您也可以將下列功能加入至專案項目：  
  
-   將捷徑功能表項目加入至專案項目。  功能表項目會在您開啟專案項目的捷徑功能表上 \[**方案總管**\] 以滑鼠右鍵按一下專案項目或藉由選取然後選擇 SHIFT \+ F10 鍵。  如需詳細資訊，請參閱[How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)。  
  
-   將自訂屬性加入至專案項目。  當您在 \[ \[**方案總管**\] 時，專案項目的屬性會出現在 \[**屬性**\] 視窗。  如需詳細資訊，請參閱[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 若要讓其他開發人員在 Visual Studio 中使用您的專案項目，請建立 .spdata 檔案，並建立與專案項目關聯的項目範本或專案範本。  如需詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## 了解專案項目類型和專案項目執行個體之間的關聯性  
 當您定義 SharePoint 專案項目類型時，Visual Studio 會在將相關類型的專案項目加入至 SharePoint 專案時載入擴充功能。  例如，如果您定義新的 \[**自訂動作**\] 專案項目類型，則當使用者將 \[**自訂動作**\] 專案項目加入至專案時，Visual Studio 會載入擴充功能。  Visual Studio 會針對相關專案項目類型的所有執行個體，使用您的擴充功能中相同的執行個體。  在前述範例中，如果使用者將第二個 \[**自訂動作**\] 專案項目加入至專案，則會使用擴充功能的相同執行個體來自訂第二個專案項目。  
  
 若要存取特定的專案項目類型執行個體，請在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法實作中，處理 *projectItemTypeDefinition* 參數的其中一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件。  例如，若要判斷何時將自訂類型的專案項目加入至專案，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。  如需詳細資訊，請參閱[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## 請參閱  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  