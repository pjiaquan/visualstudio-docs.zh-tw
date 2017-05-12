---
title: "Calling into the SharePoint Object Models"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  當您建立 SharePoint 工具的擴充功能，在 Visual Studio 中時，您可能需要呼叫 SharePoint 的 Api，以執行某些工作。  例如，如果建立 SharePoint 專案的自訂部署步驟，則可能必須呼叫 SharePoint API 執行某些工作才能部署方案。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供兩種不同的物件模型，可讓您在 SharePoint 工具擴充功能中使用：伺服器物件模型和用戶端物件模型。  每種物件模型在 SharePoint 工具擴充功能環境下都有優缺點。  
  
 如需 SharePoint 物件模型的概觀，請參閱[Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)。  
  
## 在擴充專案中使用用戶端物件模型  
 當您為 SharePoint 工具開發擴充功能時，可以在專案中使用用戶端物件模型，就如同任何其他 Managed API 集一般。  您可以將用戶端物件模型中組件的參考加入至專案，也可以在用戶端物件模型中直接從程式碼呼叫 API。  
  
 但是，用戶端物件模型在 SharePoint 工具擴充功能的內容中有兩個缺點：  
  
-   用戶端物件模型只提供伺服器物件模型的子集。  如果您需要使用未在用戶端物件模型中公開的 SharePoint 功能，則必須使用伺服器物件模型。  
  
-   雖然大部分情況下應該能夠在 SharePoint 工具擴充功能中使用用戶端物件模型，但是可能會遇到某些情況下，無法順利呼叫用戶端物件模型。  用戶端物件模型是專為用於在用戶端應用程式中呼叫遠端伺服器或伺服器陣列上的 SharePoint 網站而設計。  而 Visual Studio 中的 SharePoint 工具僅適用開發電腦上的本機 SharePoint 安裝。  因此，當您在 SharePoint 工具擴充功能中使用用戶端物件模型時，會呼叫本機電腦上的 SharePoint 網站，而這不是用戶端物件模型設計使用的方式。  
  
 示範如何使用用戶端物件模型中副檔名為 Visual Studio 的 SharePoint 工具逐步解說中，請參閱[Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## 在擴充專案中使用伺服器物件模型  
 伺服器物件模型是用戶端物件模型的超集。  當您使用伺服器物件模型時，可以透過程式設計的方式使用 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供的所有功能。  
  
 SharePoint 工具擴充功能可以在伺服器物件模型中使用 API，但是無法直接呼叫 API。  伺服器物件模型只能從目標為 .NET Framework 3.5 的 64 位元處理序呼叫。  不過，SharePoint 工具擴充功能需要 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，而且是在 32 位元的 Visual Studio 處理序中執行。  如此可避免 SharePoint 工具擴充直接參考 SharePoint 伺服器物件模型中的組件。  
  
 如果您要在 SharePoint 工具擴充功能中使用伺服器物件模型，則必須建立自訂的「*SharePoint 命令*」\(SharePoint Command\) 來呼叫 API。  您可以在能夠直接呼叫伺服器物件模型的次要組件中定義 SharePoint 命令。  在擴充專案中，您可以使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 物件的 ExecuteCommand 方法間接呼叫 SharePoint 命令。  
  
 如需建立和使用 SharePoint 命令的詳細資訊，請參閱 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)和 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)。  如需如何部署 SharePoint 命令的詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
 如需示範如何建立和使用 SharePoint 命令的逐步解說，請參閱[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)和[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
### 了解執行 SharePoint 命令的方式  
 定義 SharePoint 命令的組件會在名為 vssphost4.exe 的 64 位元主機處理序載入。  在 SharePoint 工具擴充功能中呼叫 SharePoint 命令之後，執行該命令的會是 vssphost4.exe，而不是 32 位元的 Visual Studio 處理序 \(devenv.exe\)。  您可以藉由設定登錄中的值，在某些層面上控制 SharePoint 命令的執行方式。  如需詳細資訊，請參閱[Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  