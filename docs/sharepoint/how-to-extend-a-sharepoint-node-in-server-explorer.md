---
title: "How to: Extend a SharePoint Node in Server Explorer"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  您可以在 \[**伺服器總管**\] 的 \[**SharePoint 連接**\] 節點下方擴充節點。  當您希望將新的子節點、捷徑功能表或屬性加入至現有節點時，這樣做將會很有用。  如需詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
### 若要在 \[伺服器總管\] 中擴充 SharePoint 節點  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面的類別。  
  
4.  請將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入至類別。  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 型別傳遞至屬性建構函式。  
  
5.  請將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 屬性加入至類別。  此屬性會指定要擴充之節點型別的字串識別碼。  
  
     若要指定 Visual Studio 所提供的內建節點型別，請將下列其中一個列舉值傳遞至屬性建構函式：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用這些值以指定網站連接節點 \(即顯示網站 URL 的節點\)、網站節點或 \[**伺服器總管**\] 中的所有其他父節點。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用這些值以指定其中一個內建節點，這些節點表示 SharePoint 網站上的個別元件，例如表示清單、欄位或內容類型的節點。  
  
6.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> 方法的實作中，使用 *nodeType* 參數的成員，將功能加入至節點。  這個參數是 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 物件，可用來存取 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 介面中定義的事件。  例如，您可以處理下列事件：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>：處理此事件，以將新的子節點加入至節點。  如需詳細資訊，請參閱 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>：處理此事件，以將自訂捷徑功能表項目加入至節點。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>：處理此事件，以將自訂屬性加入至節點。  當選取節點時，屬性會顯示在 \[**屬性**\] 視窗中。  
  
## 範例  
 下列程式碼範例示範如何建立兩個不同類型的節點擴充功能：  
  
-   可將內容功能表項目加入至 SharePoint 網站節點的擴充功能。  當您按一下功能表項目時，它會顯示所按節點的名稱。  
  
-   可將 \[**ContosoExampleProperty**\] 自訂屬性加入至每個代表 \[**Body**\] 欄位之節點的擴充功能。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 此擴充功能會將可編輯字串屬性加入至節點。  您也可以建立自訂屬性，顯示來自 SharePoint 伺服器的唯讀資料。  如需示範這個作法的範例，請參閱[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## 部署擴充功能  
 若要部署 \[**伺服器總管**\] 擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  