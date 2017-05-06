---
title: "Associating Custom Data with SharePoint Tools Extensions"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  您可以在 SharePoint 工具擴充功能的某些物件中加入自訂資料。  當您的一部分擴充功能中具有資料，且要在稍後從課程功能的其他程式碼存取，這將非常有用。  無需實作自訂方式來儲存和存取資料，您可以建立資料與擴充功能中物件的關聯，然後可在以後從相同物件擷取資料。  
  
 當您要保留 Visual Studio 中與特定項目相關的資料時，在物件中加入自訂資料也是很有用的。  SharePoint 工具擴充功能只會在 Visual Studio 中載入一次，所以擴充功能可隨時與多個不同項目 \(例如專案、專案項目或 **Server Explorer** 節點\) 搭配使用。  如果具有只與特定項目相關的自訂資料，您可以在表示該項目的物件中加入資料。  
  
 在 SharePoint 工具擴充功能的物件中加入自訂資料時，並不會保存資料。  資料只可在物件的生命週期期間使用。  在記憶體回收收回物件之後，會遺失資料。  
  
 在 SharePoint 專案系統的擴充功能中，您也可以儲存擴充功能卸載後仍然存在的字串資料。  如需詳細資訊，請參閱[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## 可包含自訂資料的物件  
 您可以將自訂資料加入至實作 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 介面的 SharePoint 中工具物件模型的任何物件。  這個介面只會定義一個屬性，<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>，它是自訂資料物件的集合。  下列型別會實作 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>：  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## 加入和擷取自訂資料  
 若要在將自訂資料加入至 SharePoint 工具擴充功能中的物件，請取得要加入資料的物件的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性，然後使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> 方法將資料加入至物件。  
  
 若要從 SharePoint 工具擴充功能中的物件擷取自訂資料，請取得該物件的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性，然後使用下列其中一個方法：  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  如果資料物件存在，則此方法傳回 **true**，如果不存在，則傳回 **false**。  您可以使用此方法來擷取的實值型別或參考型別的執行個體。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  如果資料物件存在，則此方法會傳回它，否則如果不存在則傳回 **null**。  您使用此方法只能擷取參考型別的執行個體。  
  
 下列程式碼範例會判斷特定資料物件是否已經與專案項目產生關聯。  如果資料物件尚未與專案項目關聯，則程式碼會將物件加入至專案項目的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性。  若要在完整的範例內容中查看這個範例，請參閱 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## 請參閱  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  