---
title: "如何：新增與移除功能相依性"
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
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 功能"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：新增與移除功能相依性
  您的 SharePoint 功能可能會相依於其他功能 \(Feature\) 的功能 \(Functionality\) 或資料。  在這種情況下，可以將這些功能標示為您功能的相依性。  這樣一來，SharePoint 伺服器便可確保相依功能會在您的功能啟動之前啟動。  
  
## 加入相依性  
 您可以將其他功能加入至方案做為相依性。  這樣一來，即可確保在安裝您的功能之前，已經先安裝和啟動必要功能。  
  
#### 若要在方案中加入功能的相依性  
  
1.  開啟功能設計工具中，展開 \[**功能啟用相依性**\] 節點，然後選擇 \[**加入**\] 按鈕。  
  
2.  在 \[**加入功能啟用相依性**\] 對話方塊中，選取 \[**在方案的功能加入相依性**\] 選項按鈕，並選取您要加入為相依功能的標題，然後選擇 \[**加入**\] 按鈕。  
  
     您可以按 Ctrl 鍵，選取多個標題以加入多個功能。  
  
## 加入自訂相依性  
 您可以加入已部署在 SharePoint 伺服器上的功能做為相依性。  這樣一來，SharePoint 啟動程序便可進行檢查，確保所有相依功能都會在您的功能安裝之前啟動。  
  
#### 若要依功能 ID 加入相依性  
  
1.  開啟功能設計工具中，展開 \[**功能啟用相依性**\] 節點，然後選擇 \[**加入**\] 按鈕。  
  
2.  在 \[**加入功能啟用相依性**\] 對話方塊中，選取 \[**加入自訂相依性**\] 選項按鈕。  
  
3.  在 \[**功能 ID**\] 文字方塊中，輸入要標示為啟用相依性之功能的 GUID，然後選擇 \[**加入**\] 按鈕。  
  
## 編輯自訂相依性  
 您可以編輯先前加入的自訂相依性。  不過，方案中的相依功能只能移除，無法編輯。  
  
#### 若要變更方案中功能的相依性  
  
1.  開啟功能設計工具，然後展開 \[**功能啟用相依性**\] 節點。  
  
2.  選取您要編輯的功能名稱，然後選擇 \[**編輯**\] 按鈕。  
  
3.  在 \[**編譯自訂功能啟用相依性**\] 對話方塊中，變更標題、ID 或描述，然後選擇 \[**送出**\] 按鈕。  
  
## 移除相依性  
  
#### 若要移除方案中功能的相依性  
  
1.  在功能設計工具中，展開 \[**功能啟用相依性**\] 節點，選取您要移除的功能名稱，然後選擇 \[**移除**\] 按鈕。  
  
## 請參閱  
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  