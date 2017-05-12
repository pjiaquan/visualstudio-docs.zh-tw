---
title: "Extending SharePoint Project Items"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  如果您要將功能加入至 Visual Studio 中已安裝的 SharePoint 專案項目類型時，請建立專案項目擴充功能。  例如，您可以在 Visual Studio 中建立內建 \[**事件接收器**\] 或 \[**清單定義**\] 專案項目的擴充功能，或您可以建立自訂專案項目類型的擴充功能。  您也可以建立所有類型 SharePoint 專案項目的擴充功能。  
  
## 擴充 SharePoint 專案項目的工作  
 若要擴充專案項目，請組建 Visual Studio 擴充功能組件，以實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面。  如需詳細資訊，請參閱[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
 當您擴充專案項目時，您也可以將下列功能加入至專案項目：  
  
-   將捷徑功能表項目加入至專案項目。  功能表項目會在您開啟專案項目的捷徑功能表上 \[**方案總管**\]。  您開啟捷徑功能表中以滑鼠右鍵按一下專案項目或藉由選取然後選擇 SHIFT \+ F10 鍵。  如需詳細資訊，請參閱[How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)。  
  
-   將自訂屬性加入至專案項目。  當您在 \[ \[**方案總管**\] 時，專案項目的屬性會出現在 \[**屬性**\] 視窗。  如需詳細資訊，請參閱[How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)。  
  
 如需示範如何建立、部署和測試專案項目擴充功能的逐步解說，請參閱[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。  
  
## 了解專案項目擴充功能和專案項目執行個體之間的關聯性  
 當您建立專案項目擴充功能時，Visual Studio 會在將相關類型的專案項目加入至 SharePoint 專案時載入擴充功能。  例如，如果您建立 \[**事件接收器**\] 專案項目的擴充功能，則當使用者將 \[**事件接收器**\] 專案項目加入至專案時，Visual Studio 會載入擴充功能。  Visual Studio 會針對相關專案項目類型的所有執行個體，使用您的擴充功能中相同的執行個體。  在前述範例中，如果使用者將第二個 \[**事件接收器**\] 專案項目加入至專案，則會使用擴充功能的相同執行個體來自訂第二個專案項目。  
  
 若要存取正在擴充的專案項目類型執行個體，請在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法實作中，處理 *projectItemType* 參數的其中一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件。  例如，若要判斷何時將正在擴充的專案項目加入至專案，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。  如需詳細資訊，請參閱[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
## SharePoint 專案項目的識別項  
 每一個 SharePoint 專案項目都有對應的字串識別項。  您必須知道專案項目的識別項，才能執行下列工作：  
  
-   建立專案項目的擴充功能。  在此情況下，您必須將要擴充之專案項目的識別項傳遞至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的建構函式。  托要建立所有專案項目類型的擴充功能，請傳遞 **\*** 字串值。  
  
-   以程式設計方式將專案項目加入至專案。  在此情況下，您必須將專案項目的識別項傳遞至 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> 方法。  
  
 下表列出隨附於 Visual Studio 中的 SharePoint 專案項目的識別項。  
  
|專案項目名稱|字串識別項|  
|------------|-----------|  
|商務資料目錄模型|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|內容類型|Microsoft.VisualStudio.SharePoint.ContentType|  
|事件接收器|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空元素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|清單定義<br /><br /> 內容類型中的清單定義|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|清單執行個體|Microsoft.VisualStudio.SharePoint.ListInstance|  
|模組|Microsoft.VisualStudio.SharePoint.Module|  
|循序工作流程<br /><br /> 狀態機器工作流程|Microsoft.VisualStudio.SharePoint.Workflow|  
|網站定義|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|視覺 Web 組件|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web 組件|Microsoft.VisualStudio.SharePoint.WebPart|  
|工作流程關聯表單|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## 請參閱  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  