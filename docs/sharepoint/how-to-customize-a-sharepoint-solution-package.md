---
title: "如何：自訂 SharePoint 方案套件 | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 套件"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：自訂 SharePoint 方案套件
  您可以使用封裝設計工具建立和自訂封裝 \(.wsp\)。  例如，您可以加入 SharePoint 專案項目和功能、指定部署方案時是否重設 Web 伺服器，以及設定部署伺服器類型。  
  
## 開啟封裝設計工具  
  
#### 若要開啟封裝設計工具  
  
-   在 \[**方案總管**\] 中，按兩下 \[**封裝**\] 或選擇 \[**封裝**\] 的捷徑功能表上的 \[**檢視表設計工具**\]。  
  
## 檢視封裝的資訊清單檔  
 您可以使用封裝設計工具修改和產生封裝的資訊清單檔。  然後您可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### 若要檢視 XML 原始程式檔  
  
1.  在 \[**封裝設計工具**\] 中，選取 \[**資訊清單**\]。  
  
#### 若要使用方案總管檢視封裝的資訊清單檔  
  
1.  在 \[**方案總管**\] 中選取 \[**顯示所有檔案**\]。  
  
2.  展開套件，展開 Package.package，然後開啟 Package.Template.xml 檔案。  
  
    > [!NOTE]  
    >  當您開啟封裝範本的資訊清單 XML 檔案時，檔案會自動進行驗證，而您可以忽略出現在 \[錯誤清單\] 視窗中的警告。  
  
## 變更資訊清單範本  
 您可以在 Visual Studio \[XML 編輯器\] 或 \[資訊清單範本\] 窗格中變更封裝資訊清單檔的 XML 程式碼。  對 XML 程式碼所做的任何變更會合併至封裝的封裝資訊清單檔。  
  
#### 若要使用 XML 編輯器變更資訊清單範本  
  
1.  在 \[**封裝設計工具**\] 中，選取 \[**資訊清單**\] 索引標籤，展開 \[**編譯選項**\] 節點，然後選擇 \[**在 XML 編輯器開啟**\] 連結。  
  
     對 XML 所做的變更會合併至封裝的資訊清單檔。  
  
#### 若要使用資訊清單範本窗格變更資訊清單範本  
  
1.  在 \[**封裝設計工具**\] 中，選取 \[**資訊清單**\] 索引標籤，展開 \[**編譯選項**\] 節點，然後變更出現在資訊清單範本窗格中的 XML。  
  
     對 XML 所做的變更會出現在 \[**預覽封裝的資訊清單**\] 窗格中。  
  
## 覆寫封裝的資訊清單檔  
 您可以停用封裝設計工具並手動建立 manifest.xml 檔案。  第一次執行此程序時，封裝設計工具中的目前設定會儲存至封裝範本 XML 檔案。  然後您可以修改或覆寫 XML 程式碼。  
  
> [!NOTE]  
>  在封裝設計工具停用時，如果您在 XML 檔案中加入或移除 SharePoint 專案項目和功能，這些專案項目和功能不會封裝。  
  
#### 若要停用設計工具來覆寫封裝的資訊清單檔  
  
1.  在 \[**封裝設計工具**\] 中，選擇 \[**資訊清單**\] 索引標籤。  
  
2.  .  
  
3.  展開 \[**編譯選項**\] 節點，選取 \[**覆寫產生的 XML 並在 XML 編輯器編輯資訊清單**\] 連結，然後選擇 \[**是**\] 按鈕。  
  
     範本便會以目前的封裝資訊清單檔更新。  
  
## 啟用封裝設計工具  
 您可以重新啟用封裝設計工具來自訂 manifest.xml 檔案。  
  
#### 若要重新啟用設計工具  
  
1.  在 \[**封裝設計工具**\] 中，選擇 \[**捨棄資訊清單編輯並重新啟用設計工具**\] 連結，然後選擇 \[**是**\] 按鈕。  
  
     範本便會以原始文字重新整理，對 XML 所做的任何變更會遺失。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  