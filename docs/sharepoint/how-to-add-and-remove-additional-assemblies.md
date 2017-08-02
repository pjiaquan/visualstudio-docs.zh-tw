---
title: "如何：新增與移除其他組件"
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
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 程式開發，套件"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：新增與移除其他組件
  如果 SharePoint 封裝相依於其他組件的功能或資料，您可以將組件加入至方案套件 \(.wsp\)。  這樣一來，SharePoint 伺服器便可確定自訂組件會隨封裝一起安裝。  
  
 您也可以加入和變更與組件相關聯的安全控制項和類別資源檔。  
  
## 加入其他組件、安全控制項和類別資源  
 您可以將其他組件加入至 SharePoint 方案套件。  沙箱化方案中的其他組件會部署至全域組件快取，但沙箱化方案中的 SharePoint 專案項目會加入至內容資料庫。  您也可以將安全控制項和類別資源加入至這些其他組件。  如需安全控制項的詳細資訊，請參閱 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 或「建立 SafeControl 輸入」 [部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=245505)。  
  
#### 若要加入現有組件  
  
1.  開啟 \[**封裝設計工具**\]。  如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選取 \[**進階**\] 索引標籤。  
  
3.  選擇 **加入**\]按鈕，並從清單中選擇 **加入現有組件** 。  
  
     \[**加入現有組件**\] 對話方塊隨即出現。  
  
4.  選擇省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\)，然後選擇想要加入的組件。  建議您使用相對於選取之組件的相對路徑，以方便移植。  
  
5.  針對 **部署目標**，選擇 **GlobalAssemblyCache** 將組件部署至全域組件快取，或選擇 **WebApplication** 將組件部署至執行 SharePoint 伺服器上 WebApplication 資料夾。  
  
#### 若要從專案輸出加入組件  
  
1.  開啟 \[**封裝設計工具**\]。  
  
     如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選取 \[**進階**\] 索引標籤。  
  
3.  選擇 **加入** 按鈕，從清單中選擇 **從專案輸出加入組件** 。  
  
     \[**從專案輸出加入組件**\] 對話方塊隨即出現。  
  
4.  在 **來源專案**清單中，選取您想要加入的來源專案。  
  
5.  針對 **部署目標**，選擇 **GlobalAssemblyCache** 將組件部署至全域組件快取，或選擇 **WebApplication** 將組件部署至執行 SharePoint 伺服器上 WebApplication 資料夾。  
  
#### 若要加入安全控制項  
  
1.  開啟 \[**編輯現有組件**\] 對話方塊。  若要完成這項作業，請開啟 封裝設計工具，選擇 **進階** 索引標籤，選取組件，然後選擇 **編輯**。  
  
2.  在 **安全控制項** 窗格中，選擇 **按一下這裡加入新項目** 按鈕。  
  
3.  在 **組件名稱** 欄中，輸入組件的名稱。  
  
4.  在 **命名空間** 欄中，輸入安全控制項的命名空間名稱。  
  
5.  在 **型別名稱** 欄中，輸入型別的名稱。  
  
#### 若要加入類別資源  
  
1.  開啟 \[**編輯現有組件**\] 對話方塊。  若要完成這項作業，請開啟 封裝設計工具，選擇 **進階** 索引標籤，選取組件，然後選擇 **編輯**。  
  
2.  在 **類別資源** 窗格中，選擇 **按一下這裡加入新項目**。  
  
3.  在 \[**檔案名稱**\] 欄中，選擇省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\)，然後選取想要加入的類別資源。  
  
## 刪除自訂組件  
 您可以從 SharePoint 封裝刪除組件，或從現有組件刪除安全控制項和類別資源。  
  
#### 若要刪除現有組件  
  
1.  開啟 \[**封裝設計工具**\]。  如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  選取 \[**進階**\] 索引標籤。  
  
3.  在 \[**其他組件**\] 窗格中，選取想要刪除的自訂組件。  
  
4.  選擇 **刪除** 按鈕。  
  
#### 若要刪除組件的安全控制項  
  
1.  開啟 \[**編輯現有組件**\] 對話方塊。  若要完成這項作業，請開啟 封裝設計工具，選擇 **進階** 索引標籤，選取組件，然後選擇 **編輯**。  
  
2.  選擇您要刪除的安全控制項。  
  
3.  選則 Delete 鍵。  
  
#### 若要刪除組件的類別資源  
  
1.  開啟 \[**編輯現有組件**\] 對話方塊。  若要完成這項作業，請開啟 封裝設計工具，選擇 **進階** 索引標籤，選取組件，然後選擇 **編輯**。  
  
2.  選擇您要刪除的類別資源。  
  
3.  選擇 Delete 鍵。  
  
## 請參閱  
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/zh-tw/700a570a-e98e-4425-aadd-34c014868d43)  
  
  