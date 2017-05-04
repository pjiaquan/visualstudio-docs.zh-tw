---
title: "部署、發行和升級 SharePoint 方案套件 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "部署 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 部署"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 部署、發行和升級 SharePoint 方案套件
  當您在 Visual Studio 中開發 SharePoint 方案後，您可以將它的封裝 \(.wsp\) 檔案部署到本機 SharePoint 伺服器或將它發行至遠端或本機 SharePoint 伺服器。  如果您部署檔案，您可以自訂封裝檔案 \(.wsp\) 如何部署。  
  
> [!NOTE]  
>  目前，只有沙箱化方案可以發行至遠端 SharePoint 伺服器。  如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
## 部署，發行和升級  
 *部署* 表示將在 Visual Studio 中建置的 SharePoint 專案檔案複製到本端主機。  在部署的方案中，您可以設定部署步驟，例如回收 Internet Information Services \(IIS\) 集區、在部署之後啟動方案等等。  若要部署，請使用 \[**建置**\] 功能表上的 \[**部署**\] 命令。  如需詳細資訊，請參閱[如何：編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)與[如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 *發行* 是指載入沙箱 SharePoint 方案檔案到遠端 SharePoint 網站；也就是位於另一個系統的網站。  您也可以發行 SharePoint 沙箱化方案檔案到本機 SharePoint 網站，不過，不論該網站是否發行至本機或遠端，您都無法設定其部署步驟。  
  
 *升級* 是指更新存在遠端或發行在本機的 SharePoint 方案。  在 Visual Studio 中對 SharePoint 方案進行任何變更後，您在成功重新發佈方案之後變更方案的封裝檔案名稱、重新發行方案，然後升級方案。  如果您重新發行本機發行的方案，您可以覆寫現有的方案檔。  
  
## 部署封裝  
 您可以將封裝檔案部署至開發電腦上的 SharePoint 伺服器，以便進行測試和偵錯。  您也可以經由選取 \[**發行**\] 對話方塊的 \[**發行至檔案系統**\] 選項按鈕，建立可在其他電腦上安裝的封裝檔案。  封裝已建立並複製到指定的本機檔案路徑。  若要將 SharePoint 方案部署至本機伺服器，請在 \[**建置**\] 功能表上的 \[**部署**\] 命令。  如需詳細資訊，請參閱[如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)。  
  
 若要了解如何部署清單定義、加入事件接收器，以及使用「功能設計工具」和「封裝設計工具」，請參閱[逐步解說：部署專案工作清單定義](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)。  
  
## 自訂部署程序  
 下表顯示偵錯和部署 SharePoint 方案時可以使用的兩種部署組態。  
  
|部署組態|說明|  
|----------|--------|  
|預設|預設部署組態。  系統會執行下列部署步驟：<br /><br /> 1.  執行預先部署命令。<br />2.  回收 IIS 應用程式集區。<br />3.  撤銷方案。<br />4.  加至方案。<br />5.  啟動功能。<br />6.  執行部署後命令。<br /><br /> 解除安裝封裝時，會執行下列撤銷步驟。<br /><br /> 1.  回收 IIS 應用程式集區。<br />2.  撤銷方案。|  
|不啟動|這個部署組態執行的步驟與 \[預設\] 組態相同，但會略過啟動步驟。|  
  
 您可以自行建立部署組態來完成單一步驟，或變更部署程序中的步驟順序。  如需詳細資訊，請參閱[如何：編輯 SharePoint 部署組態](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
 您也可以加入要在部署之前和之後執行的命令。  如需詳細資訊，請參閱[如何：設定 SharePoint 部署命令](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。  
  
## 發行封裝至遠端或本機伺服器  
 若要發行沙箱 SharePoint 方案至遠端伺服器，在功能表列上，請選擇 \[**建置**\]、\[**發行**\]，然後在 \[**發行**\] 對話方塊中，選取 \[**發行至 SharePoint 網站**\] 選項按鈕，提供遠端伺服器的 URL，例如 https:\/\/someremoteserver.sharepoint.microsoftonline.com。  
  
 若要發行 SharePoint 方案至本機伺服器，在 \[**發行**\] 對話方塊中，選取 \[**發行至本機檔案系統**\] 選項按鈕，提供本機系統路徑。  
  
 在成功發行方案至 SharePoint 後，方案會顯示在 \[**方案庫**\]，您可以在此啟動它。  如需詳細資訊，請參閱[如何：在遠端伺服器部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
### 升級發行的封裝  
 方案發行後，如果您在 Visual Studio 中對 SharePoint 專案進行任何變更，發行的封裝必須升級，以包含這些內變更。  若要升級成功，套件必須具有唯一的名稱。  如果 SharePoint 網站上找到具有相同名稱的封裝 \(當您更新現有應用程式時可能發生\)，會顯示錯誤，警告您檔案名稱的衝突，並讓您為套件重新命名。  在被重新發行之後，新的封裝出現在 SharePoint 網站，且可以升級。  升級的套件使用舊版套件的資料更新方案，然後在 SharePoint 中啟動方案。  如需詳細資訊，請參閱[如何：在遠端伺服器部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  