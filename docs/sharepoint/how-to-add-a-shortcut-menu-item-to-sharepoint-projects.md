---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects | Microsoft Docs"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  您可以將捷徑功能表項目加入至任何 SharePoint 專案。  使用者在 \[**方案總管**\] 中以滑鼠右鍵按一下專案節點時，就會出現功能表項目。  
  
 下列步驟假設您已經建立專案擴充功能。  如需詳細資訊，請參閱 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### 若要將捷徑功能表項目加入至 SharePoint 專案  
  
1.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 實作之 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法中，請處理 *projectService* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 事件。  
  
2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> 事件的事件處理常式中，將新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件加入至事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> 或 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> 集合。  
  
3.  在新 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 事件處理常式中，執行在使用者按一下捷徑功能表項目時要執行的工作。  
  
## 範例  
 下列程式碼範例示範如何將捷徑功能表項目加入至 \[**方案總管**\] 中的 SharePoint 專案節點。  當使用者以滑鼠右鍵按一下專案節點，並且按一下 \[**將訊息寫入輸出視窗**\] 功能表項目時，Visual Studio 會在 \[**輸出**\] 視窗中顯示訊息。  此範例使用 SharePoint 專案服務來顯示訊息。  如需詳細資訊，請參閱 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## 編譯程式碼  
 這個範例需要類別庫專案並參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  