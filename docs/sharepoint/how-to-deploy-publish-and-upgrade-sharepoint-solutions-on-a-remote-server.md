---
title: "如何：在遠端伺服器部署、發行和升級 SharePoint 方案"
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
  - "部署 [Visual Studio 中的 SharePoint 開發]"
  - "遠端部署 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 部署"
  - "Visual Studio 中的 SharePoint 開發, 遠端部署"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在遠端伺服器部署、發行和升級 SharePoint 方案
  除了部署 SharePoint 方案到本機系統之外，您可以發行沙箱 SharePoint 方案至遠端網站或本機 SharePoint 網站。  遠端發行處理序複製 .wsp 檔到 SharePoint 伺服器上，安裝方案，然後讓您可以啟動方案。  您也可以在變更它之後升級遠端 SharePoint 方案安裝。  
  
## 若要發行沙箱 SharePoint 方案至遠端 SharePoint 伺服器  
  
1.  在 \[**方案總管**\] 中，開啟您要發佈的沙箱 SharePoint 專案的捷徑功能表，然後選擇 \[**發行**\]。  
  
2.  在 \[**發行**\] 對話方塊中，選取 \[**發行至 SharePoint 網站**\] 選項按鈕，然後輸入一個線上發行網站的 URL，例如下列範例：https:\/\/mytestsite.sharepoint.microsoftonline.com。  
  
3.  選取 \[**發行之後在瀏覽器中開啟方案庫頁面**\] 選項按鈕，以在發行之後檢視 \[**方案庫**\] 頁面的方案清單。  
  
4.  選擇 \[**發行**\] 按鈕。  
  
5.  如果需要使用者認證，請登入遠端伺服器。  
  
     發行進度出現在 Visual Studio 的 \[**輸出**\] 視窗。  當處理序完成時，方案 \(.wsp\) 檔案已安裝在遠端 SharePoint 伺服器。  不過，若要在 SharePoint 中使用，仍然必須先啟動它。  
  
6.  在 \[**方案庫**\] 頁面上，選取 SharePoint 應用程式，然後在功能區上選擇 \[**啟動**\] 按鈕。  
  
7.  在 \[**啟動方案**\] 對話方塊中，在功能區上再選擇 \[**啟動**\] 按鈕。  
  
     在 \[**方案庫**\] 頁面的 \[**狀態**\] 欄會顯示應用程式正在作用中。  
  
## 若要在遠端 SharePoint 伺服器升級沙箱 SharePoint 方案  
 如果沙箱 SharePoint 方案已在遠端伺服器上發行，下列程序可讓您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中對應用程式進行變更後，將它升級。  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中重新命名 SharePoint 封裝。  若要這麼做，請在 \[**方案總管**\] 中開啟封裝。  它會出現在 \[**封裝總管**\]。  
  
2.  在 \[**封裝總管**\] 的 \[**名稱**\] 方塊中，將套件名稱變更為唯一的名稱。  
  
3.  儲存專案。  
  
4.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**發行**\]。  
  
5.  在 \[**發行**\] 對話方塊中，選取 \[**發行至 SharePoint 網站**\] 選項按鈕，如果儲存方案的遠端伺服器的 URL 已遺失，請輸入它。  
  
6.  選取 \[**發行之後在瀏覽器中開啟方案庫頁面**\] 選項按鈕，以在發行之後檢視 \[**方案庫**\] 頁面的方案清單。  
  
7.  選擇 \[**發行**\] 按鈕。  
  
8.  如果需要使用者認證，請登入遠端伺服器。  
  
     如果您最近已登入至遠端伺服器，可能不需要驗證。  
  
     如果仍然有相同名稱的應用程式的舊版本存在於 SharePoint 伺服器，您會得到錯誤，顯示有相同名稱的套件已經存在於 SharePoint 伺服器。  您必須在發行之前為套件重新命名。  
  
9. 在 SharePoint 中建立新的應用程式，然後在功能區上，選擇 \[**升級**\] 按鈕。  
  
10. 在 \[**升級方案**\] 對話方塊中，在功能區上再選擇 \[**升級**\] 按鈕。  在 \[**方案庫**\] 頁面的 \[**狀態**\] 欄位，現在應該表示應用程式正在使用中。  
  
     舊版的方案已停用，擁有來自舊版方案資料的新版方案已升級，然後，新版方案已在 SharePoint 中啟動。  
  
## 請參閱  
 [如何：將 SharePoint 方案部署和發行至本機 SharePoint 網站](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [如何：使用封裝設計工具在套件中新增與移除功能](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  