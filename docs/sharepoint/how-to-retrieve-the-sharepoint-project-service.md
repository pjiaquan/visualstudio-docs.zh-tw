---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  您可以存取下列各類型方案中的 SharePoint 專案服務：  
  
-   SharePoint 專案系統的擴充功能，例如專案擴充功能、專案項目擴充功能或專案項目類型定義。  如需上述類型之擴充功能的詳細資訊，請參閱[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
-   在 \[**伺服器總管**\] 中 \[**SharePoint 連接**\] 節點的擴充功能。  如需上述類型之擴充功能的詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
-   另一個類型的 Visual Studio 擴充功能，例如增益集或 VSPackage。  
  
## 擷取專案系統擴充功能中的服務  
 在 SharePoint 專案系統的任何擴充功能中，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> 屬性存取專案服務。  
  
 您也可以利用下列程序擷取專案服務。  
  
#### 若要擷取專案擴充功能中的服務  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面的實作中，尋找 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法。  
  
2.  使用 *projectService* 參數存取服務。  
  
     下列程式碼範例示範如何使用專案服務，在簡單的專案擴充功能中將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     如需建立專案擴充功能的詳細資訊，請參閱 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
#### 若要擷取專案項目擴充功能中的服務  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面的實作中，尋找 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法。  
  
2.  使用 *projectItemType* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> 屬性來擷取服務。  
  
     下列程式碼範例示範如何使用專案服務，在簡單的 \[**清單定義**\] 專案項目擴充功能中將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     如需建立專案項目擴充功能的詳細資訊，請參閱 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
#### 若要擷取專案項目類型定義中的服務  
  
1.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的實作中，尋找 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法。  
  
2.  使用 *typeDefinition* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> 屬性來擷取服務。  
  
     下列程式碼範例示範如何使用專案服務，在簡單的專案項目類型定義中將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     如需定義專案項目類型的詳細資訊，請參閱 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## 擷取伺服器總管擴充功能中的服務  
 在 \[**伺服器總管**\] 之 \[**SharePoint 連接**\] 節點的擴充功能中，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 物件的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 屬性存取專案服務。  
  
#### 若要擷取伺服器總管擴充功能中的服務  
  
1.  在擴充功能中，從 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 物件的 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 屬性取得 <xref:System.IServiceProvider> 物件。  
  
2.  使用 <xref:System.IServiceProvider.GetService%2A> 方法來要求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。  
  
     下列程式碼範例示範如何使用專案服務，從擴充功能加入至 \[**伺服器總管**\] 中清單節點的捷徑功能表，將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     如需擴充 \[**伺服器總管**\] 中 \[**SharePoint 連接**\] 節點的詳細資訊，請參閱 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。  
  
## 擷取其他 Visual Studio 擴充功能中的服務  
 您可以在 VSPackage 中或任何 Visual Studio 擴充功能中擷取專案服務，後者具有自動化物件模型中的 <xref:EnvDTE80.DTE2> 物件，例如增益集或專案範本精靈，其會實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。  
  
 在 VSPackage 中，您可以使用下列其中一個方法要求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件：  
  
-   衍生自 <xref:Microsoft.VisualStudio.Shell.Package> 類別之 Managed VSPackage 的 <xref:System.IServiceProvider.GetService%2A> 方法。  如需詳細資訊，請參閱 [如何: 取得服務](~/extensibility/how-to-get-a-service.md)。  
  
-   靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法。  如需詳細資訊，請參閱 [如何：使用 GetGlobalService](~/misc/how-to-use-getglobalservice.md)。  
  
 在可以存取 <xref:EnvDTE80.DTE2> 物件的 Visual Studio 擴充功能中，您可以使用 <xref:Microsoft.VisualStudio.Shell.ServiceProvider> 物件的 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 方法，要求 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。  如需詳細資訊，請參閱 [如何：從 DTE 物件取得服務](~/misc/how-to-get-a-service-from-the-dte-object.md)。  
  
### 範例  
 下列程式碼範例示範如何在 Visual Studio 增益集中擷取專案服務。  若要使用這個程式碼，請在增益集專案中的 `Connect` 類別中執行該程式碼。  `_applicationObject` 物件是在增益集專案中自動產生的，這個物件是 <xref:EnvDTE80.DTE2> 介面的執行個體。  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 這個範例需要：  
  
-   Visual Studio 增益集專案。  如需詳細資訊，請參閱 [如何：建立增益集](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)。  
  
-   Microsoft.VisualStudio.OLE.Interop、Microsoft.VisualStudio.Shell 和 Microsoft.VisualStudio.SharePoint 組件的參考資料。  
  
## 請參閱  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [如何：建立增益集](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)   
 [如何: 取得服務](~/extensibility/how-to-get-a-service.md)   
 [如何：從 DTE 物件取得服務](~/misc/how-to-get-a-service-from-the-dte-object.md)   
 [如何：搭配專案範本使用精靈](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  