---
title: "How to: Create a SharePoint Command"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  如果您要在 SharePoint 工具擴充功能中使用伺服器物件模型，則必須建立自訂的「*SharePoint 命令*」\(SharePoint Command\) 來呼叫 API。  您可以在能夠直接呼叫伺服器物件模型的組件中定義 SharePoint 命令。  
  
 如需 SharePoint 命令用途的詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### 若要建立 SharePoint 命令  
  
1.  建立具有下列配置的類別庫專案：  
  
    -   將 .NET Framework 3.5 做為目標。  如需選取目標架構的詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
    -   將 AnyCPU 或 x64 平台做為目標。  類別庫專案的預設目標平台是 AnyCPU。  如需選取目標平台的詳細資訊，請參閱 [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/zh-tw/294a75d2-4279-4b72-8298-2bea05be907a)。  
  
    > [!NOTE]  
    >  您不能在定義 SharePoint 工具擴充功能的相同專案中實作 SharePoint 命令，因為 SharePoint 命令以 .NET Framework 3.5 為目標，而 SharePoint 工具擴充功能以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 為目標。  您必須在個別專案中定義由您的擴充功能使用的任何 SharePoint 命令。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  在專案的類別中，幾件案例定義 SharePoint 命令的方法。  該方法必須遵守以下方針：  
  
    -   它可以擁有一或兩個參數。  
  
         第一個參數必須是 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 物件。  此物件提供 Microsoft.SharePoint.SPSite 或 Microsoft.SharePoint.SPWeb，可在其上執行命令。  它也提供 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> 物件，可用來在 Visual Studio 中將訊息寫入 \[**輸出**\] 視窗或 \[**錯誤清單**\] 視窗。  
  
         第二個參數的型別您可自行選擇，但這個參數是選擇性的。  如果需要從 SharePoint 工具擴充功能將資料傳遞至命令，請將這個參數加入至 SharePoint 命令。  
  
    -   它可以擁有傳回值，但這是選擇性的。  
  
    -   第二個參數和傳回值的型別必須是能夠由 Windows Communication Foundation \(WCF\) 序列化的型別。  如需詳細資訊，請參閱[資料合約序列化程式支援的型別](http://msdn.microsoft.com/library/7381b200-437a-4506-9556-d77bf1bc3f34)和[使用 XmlSerializer 類別](http://msdn.microsoft.com/library/c680602d-39d3-44f1-bf22-8e6654ad5069)。  
  
    -   方法可以具有任何可視性 \(**public**、**internal** 或 **private**\)，且可以是靜態或非靜態。  
  
4.  將 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 套用至方法。  此屬性會指定命令的唯一識別項；此識別項不需要符合方法名稱。  
  
     當您從 SharePoint 工具擴充功能呼叫命令時，您必須指定相同的唯一識別項。  如需詳細資訊，請參閱 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)。  
  
## 範例  
 下列程式碼範例示範擁有 `Contoso.Commands.UpgradeSolution` 識別項的 SharePoint 命令。  此命令在伺服器物件模型中使用 API，以升級至已部署的方案。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 除了隱含的第一個 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數之外，此命令還有一個自訂的字串參數，其中包含正在升級至 SharePoint 網站的 .wsp 檔案完整路徑。  若要在完整的範例內容中查看這個程式碼，請參閱[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## 部署命令  
 若要部署命令，請將命令組建併入與使用該命令的擴充功能組件相同的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件中。  您還必須在 extension.vsixmanifest 檔案加入命令組件的項目。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  