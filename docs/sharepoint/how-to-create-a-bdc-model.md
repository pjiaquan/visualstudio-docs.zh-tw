---
title: "如何：建立 BDC 模型 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 建立模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 建立模型"
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：建立 BDC 模型
  您可以使用該範本建立該類型的項目建立商務資料連接模型 \(BDC\)，然後將模型加入至任何 SharePoint 專案。  如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  如需如何設計模型的詳細資訊，請參閱 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 若要建立 BDC 專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
    > [!NOTE]  
    >  如果您的 IDE 設定為使用 Visual Basic 開發設定，請選擇 \[**檔案**\] 功能表上的 \[**新增專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
2.  在 \[**Visual Basic**\] 或 \[**Visual C\#**\] 底下，選擇 \[**Office\/SharePoint**\]、\[**SharePoint 方案**\]。  
  
3.  在 \[**範本**\] 窗格中，選擇 \[**SharePoint 2013 \- 空專案**\] 項目，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即開啟。  
  
4.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，指定 SharePoint 網站在本機電腦上的 URL，選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕。  
  
     您將在您指定的 SharePoint 網站測試該模型。  
  
    > [!IMPORTANT]  
    >  因為 BDC 模型只支援陣列方案，因此您必須將專案部署為陣列方案。  
  
     空白 SharePoint 專案已建立。  
  
5.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
6.  在 \[**加入新項目**\] 對話方塊中，選擇 \[**Office\/SharePoint**\] 節點。  
  
7.  在 SharePoint 範本清單中，選擇 \[**商務資料連接模型 \(僅限陣列方案\)**\]。  
  
8.  在 \[**名稱**\] 方塊中指定 BDC 模型的名稱，然後選擇 \[**加入**\] 按鈕。  
  
     \[**商務資料連接模型**\] 項目隨即加入至專案。  根據預設，模型會顯示在 BDC 設計工具中。  如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## 請參閱  
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  