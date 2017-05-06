---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  針對 \[**伺服器總管**\] 的每一個內建 SharePoint 節點，您都可以取得節點所代表之基礎 SharePoint 元件的資料。  如需詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## 範例  
 下列程式碼範例示範如何取得 \[**伺服器總管**\] 中清單節點所代表之基礎 SharePoint 清單的資料。  根據預設，清單節點具有一個 \[**在瀏覽器中檢視**\] 內容功能表項目，您可以按一下該項目來開啟 Web 瀏覽器中的清單。  此範例藉由加入會在 Visual Studio 中直接開啟清單的 \[**在 Visual Studio 中檢視**\] 內容功能表項目，來擴充清單節點。  程式碼會存取節點的清單資料，以取得 Visual Studio 中所開啟清單的 URL。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 此範例會使用 SharePoint 專案服務來取得用於開啟 Visual Studio 中清單的 <xref:EnvDTE.DTE> 物件。  如需 SharePoint 專案服務的詳細資訊，請參閱[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 如需建立 SharePoint 節點擴充功能之基本工作的詳細資訊，請參閱 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署 \[**伺服器總管**\] 擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  