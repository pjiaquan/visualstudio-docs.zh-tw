---
title: "如何：使用封裝總管在套件中新增與移除功能和項目 | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 套件"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：使用封裝總管在套件中新增與移除功能和項目
  若要設定套件以部署 SharePoint 項目和功能，您可以使用「封裝總管」。  您可以調整 .wsp 檔案中的 SharePoint 專案項目和功能。  
  
 除此之外，還可以使用「封裝設計工具」檢視和重新排序功能，以變更啟動順序。  如需詳細資訊，請參閱[如何：使用封裝設計工具在套件中新增與移除功能](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。  
  
## 開啟封裝總管  
 如果您的 Visual Studio 方案至少有一個 SharePoint 專案，即可透過下列程序來開啟封裝總管。  此外，當您檢視功能或封裝設計工具時，封裝總管也會自動開啟。  當您關閉所有功能和封裝設計工具之後，封裝總管也會關閉。  
  
#### 若要開啟封裝總管  
  
1.  在功能表列上選擇 \[**檢視**\]、\[**其他視窗**\]、\[**封裝總管**\]。  
  
     \[**封裝總管**\] 隨即出現在 \[**工具箱**\] 中。  
  
## 將功能加入至封裝  
 您可以使用封裝總管，將新的和現有的功能加入至封裝。  
  
#### 若要新增 SharePoint 功能  
  
1.  開啟 \[**封裝總管**\]，開啟專案的捷徑功能表，然後選擇 \[**新增功能**\]。  
  
#### 若要移動現有的 SharePoint 功能  
  
1.  開啟 \[**封裝總管**\]，然後執行下列其中一個步驟：  
  
    -   將 \[**功能**\] 從一個專案拖曳至另一個專案。  
  
    -   開啟功能的捷徑功能表，選擇 \[**剪下**\]，開啟要移動功能的專案捷徑功能表，然後選擇 \[**貼上**\]。  
  
    > [!NOTE]  
    >  如果您的方案有一個以上的 SharePoint 專案，請使用此程序。  
  
## 驗證功能或封裝  
 您可以藉由驗證檔案，識別 SharePoint 功能和封裝中可能的問題。  警告和錯誤會顯示在 \[輸出\] 視窗和 \[錯誤清單\] 視窗中。  
  
#### 若要驗證 SharePoint 功能或封裝  
  
1.  開啟 \[**封裝總管**\]。  
  
2.  開啟功能或封裝的捷徑功能表，然後選擇 \[**驗證**\]。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  