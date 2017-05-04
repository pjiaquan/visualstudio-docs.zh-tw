---
title: "How to: Add a Custom SharePoint Node to Server Explorer | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  您可以在 \[**伺服器總管**\] 的 \[**SharePoint 連接**\] 節點下方加入自訂節點。  當您要顯示不是 \[**伺服器總管**\] 中預設顯示的其他 SharePoint 元件時，這會相當有用。  如需詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
 若要加入自訂節點，請先建立定義新節點的類別。  然後建立擴充功能，以加入節點做為現有節點的子節點。  
  
### 若要定義新節點  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面的類別。  
  
4.  將下列屬性加入到類別：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 型別傳遞至屬性建構函式。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  在節點定義中，此屬性會指定新節點的字串識別項。  建議您使用 \<*公司名稱*\>.\<*節點名稱*\> 格式，以確保所有節點都有唯一的識別項。  
  
5.  在您的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> 方法實作中，使用 *typeDefinition* 參數的成員來設定新節點的行為。  這個參數是 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> 物件，可用來存取 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> 介面中定義的事件。  
  
     下列程式碼範例將示範如何定義新的節點。  此範例假設您的專案包含名為 CustomChildNodeIcon 的圖示做為內嵌資源。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### 若要加入新節點做為現有節點的子節點  
  
1.  在節點定義所在的相同專案中，建立實作 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面的類別。  
  
2.  請將 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性加入至類別。  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 型別傳遞至屬性建構函式。  
  
3.  請將 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> 屬性加入至類別。  在節點擴充功能中，此屬性會指定要擴充之節點型別的字串識別項。  
  
     若要指定 Visual Studio 所提供的內建節點型別，請將下列其中一個列舉值傳遞至屬性建構函式：  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>：使用這些值以指定網站連接節點 \(即顯示網站 URL 的節點\)、網站節點或 \[**伺服器總管**\] 中的所有其他父節點。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>：使用這些值以指定其中一個內建節點，這些節點表示 SharePoint 網站上的個別元件，例如表示清單、欄位或內容類型的節點。  
  
4.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> 方法的實作中，處理 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> 參數的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 事件。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> 事件處理常式中，將新節點加入至事件引數參數所公開之 <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> 物件的子節點集合。  
  
     下列程式碼範例示範如何在 \[**伺服器總管**\] 中加入新節點做為 SharePoint 網站節點的子節點。  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## 完整範例  
 下列程式碼範例提供完整的程式碼，首先定義簡單的節點，再將它加入 \[**伺服器總管**\] 中做為 SharePoint 網站節點的子節點。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## 編譯程式碼  
 此範例假設您的專案包含名為 CustomChildNodeIcon 的圖示做為內嵌資源。  此外，這個範例還需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## 部署擴充功能  
 若要部署 \[**伺服器總管**\] 擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  