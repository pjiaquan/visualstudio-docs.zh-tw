---
title: "Extending the SharePoint Connections Node in Server Explorer"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  Visual Studio中，您可以在區域的 SharePoint 網站，在開發電腦上的 \[連線使用 **SharePoint 連線** 中的節點**伺服器總管**視窗。   此節點會在階層樹狀檢視中，顯示本機 SharePoint 網站的許多元件。  例如，您可以檢視本機網站上的清單、文件庫和內容類型。如需使用 \[**伺服器總管**\] 連接到本機 SharePoint 網站的詳細資訊，請參閱[使用伺服器總管瀏覽 SharePoint 連線](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)。  
  
 藉由建立現有節點的擴充功能，或建立自訂節點類型並將其加入至節點的階層架構，即可擴充 \[**SharePoint 連接**\] 節點。  
  
## 擴充 SharePoint 連接節點的工作  
 若要擴充現有節點，請建立 Visual Studio 擴充功能，以實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面。  當您擴充節點時，可以將功能 \(例如，自己的捷徑功能表項目或自訂屬性\) 加入至節點。  如需詳細資訊，請參閱 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
 若要建立自訂節點類型，請建立 Visual Studio 擴充功能，以實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面。  如果您要顯示不是 \[**伺服器總管**\] 中預設顯示的 SharePoint 網站元件，請建立自訂節點。  例如，\[**伺服器總管**\] 預設不會顯示 SharePoint 網站的 Web 組件庫，但是您可以加入執行這項操作的自訂節點。  如需詳細資訊，請參閱 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)和[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## 將自訂屬性加入至節點  
 當您擴充節點或建立自訂節點類型時，可以將自訂屬性加入至節點。  當選取節點時，屬性會顯示在 \[**屬性**\] 視窗中。  
  
 您可以加入至節點的自訂屬性有兩種類型：  
  
-   顯示一組來自 SharePoint 網站之唯讀資料的屬性。  此資料描述節點所表示的 SharePoint 元件。  如需示範如何這麼做的逐步解說，請參閱[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   顯示自訂讀取\/寫入資料的屬性。  如需示範這個做法的程式碼範例，請參閱 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 取得內建節點的資料  
 Visual Studio 提供的所有內建節點都包含一些其所表示之 SharePoint 元件的資料。  例如，表示 SharePoint 網站中清單的節點會提供一些有關該清單的資料，例如清單之預設檢視的標題和 URL。  
  
 若要存取這項資料，請從表示您所需節點之 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 物件的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性中擷取資料物件。  資料物件的型別取決於節點的類型。  
  
 下列程式碼範例示範如何取得清單節點的資料物件。  若要在完整的範例內容中查看這個範例，請參閱 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 下表列出每個內建節點類型的資料物件型別。  
  
|節點類型|資料物件型別|  
|----------|------------|  
|SharePoint 網站節點|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|內容類型|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|功能|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|欄位|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|清單範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|清單檢視 \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|工作流程關聯|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|工作流程範本|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性的詳細資訊，請參閱 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## 請參閱  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [使用伺服器總管瀏覽 SharePoint 連線](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  