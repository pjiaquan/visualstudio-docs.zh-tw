---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Visual Studio中的工具 Visual\\ 許多應用程式開發案例的需求。  不過，您可能發現在某些情況下，這些工具並未提供您或其他開發人員所需的功能。  在這些情況下，您可以擴充 SharePoint 工具以建立所需的功能。  
  
## 如何擴充 SharePoint 工具  
 您可以在 \[**伺服器總管**\] 視窗中，擴充 SharePoint 專案系統和 \[**SharePoint 連接**\] 節點。  
  
### 擴充 SharePoint 專案系統  
 Visual Studio包含了一組專案範本和項目範本，您可以用來建立SharePoint 解決方案。  例如，這些範本可用於事件接收器、清單定義、工作流程和 Web 組件。  但您也可以定義您自己的 SharePoint 專案項目型別，用以建立欄位或自訂動作等 SharePoint 元件。  您也可以為已安裝於 Visual Studio 中的 SharePoint 專案項目型別建立擴充功能，以及為 SharePoint 專案建立擴充功能。  
  
 如需詳細資訊，請參閱[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
### 在伺服器總管中擴充 SharePoint 連接節點  
 在Visual Studio中，您可以使用 **SharePoint 連線** 中的節點**伺服器總管** \]視窗來檢視許多元件的其中一個或多個區域SharePoint 網站階層式樹狀檢視中。您也可以擴充  **SharePoint 連線**節點以下列方式：  
  
-   加入自己的節點。  如果您要顯示非預設顯示的 SharePoint 網站元件，這會相當有用。  
  
-   擴充現有節點。  例如，您可以將新的子節點加入至現有的節點，或是將捷徑功能表項目加入至節點而在開發人員按一下功能表項目時執行工作。  
  
 如需詳細資訊，請參閱[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。  
  
## 開發電腦需求  
 若要建立副檔名與 SharePoint 工具開發軟體的電腦必須符合相同的需求，在Visual Studio建立 SharePoint 解決方案。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
 此外，也建議您安裝 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  SDK 包括專案範本和工具，可讓您用來擴充 Visual Studio。  特別是，SDK 中的專案範本可讓您輕鬆地建立 Visual Studio Extension \(VSIX\) Package。  VSIX 套件是部署在Visual StudioVisual Studio擴充功能的慣用的方法。   所有 SharePoint 工具擴充功能都必須使用 VSIX 套件來部署。  本文件中所有的逐步解說會假設您已安裝 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  
  
 若要下載 SDK，請參閱 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562) \(英文\)。  如需 Visual Studio 擴充功能的詳細資訊，請參閱[開發 Visual Studio 擴充功能](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14)。  
  
## 請參閱  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  