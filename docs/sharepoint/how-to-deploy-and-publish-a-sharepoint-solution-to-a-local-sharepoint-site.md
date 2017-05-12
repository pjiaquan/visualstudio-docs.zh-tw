---
title: "如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "部署 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 部署"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站
  您可以將 SharePoint 方案部署或發佈至開發電腦上的本機 SharePoint 伺服器。  部署程序會將 .wsp 檔案複製到 SharePoint 伺服器、安裝方案，然後啟動功能。  發行處理序只複製 .wsp 檔複製到 SharePoint 伺服器並安裝它。  您必須手動啟動它，讓它在 SharePoint 啟用。  
  
## 若要將 SharePoint 方案部署至本機 SharePoint 伺服器  
  
1.  在 \[**方案總管**\] 中，選擇您要部署的專案。  
  
2.  在功能表列上，選擇 \[**建置**\]、\[**部署方案**\]。  
  
     .wsp 檔案隨即會建立並安裝在本機 SharePoint 伺服器上。  此外也會啟動功能。  
  
## 若要將 SharePoint 方案發佈至本機 SharePoint 伺服器  
  
1.  在 \[**方案總管**\] 中，開啟您要發佈的 SharePoint 專案的捷徑功能表，然後選擇 \[**發行**\]。  
  
2.  在 \[**發行**\] 對話方塊中，選取 \[**對檔案系統的發行**\] 選項按鈕。  
  
3.  在 \[**目標位置**\] 文字方塊中，輸入本機路徑，然後選擇 \[**發行**\] 按鈕。  
  
     發行進度出現在 Visual Studio 的 \[**輸出**\] 視窗。  當處理序完成時，方案 \(.wsp\) 檔案已安裝在本機 SharePoint 伺服器。  不過，仍然必須啟用它，以便可以在 SharePoint 中使用。  如果方案檔已存在，則會發生錯誤並詢問您是否要覆寫現有的檔案。  如需升級套件的詳細資訊，請參閱 [如何：在遠端伺服器部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md) 中有關升級遠端套件的部分。  
  
## 請參閱  
 [如何：在遠端伺服器部署、發行和升級 SharePoint 方案](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用封裝設計工具在套件中新增與移除功能](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  