---
title: "如何：自訂 SharePoint 功能"
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
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 功能"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：自訂 SharePoint 功能
  您可以使用 Visual Studio 中的「功能設計工具」，建立和自訂 SharePoint 功能。  例如，您可以設定功能範圍並加入其他功能做為相依性。  依預設，當您在「方案總管」或 SharePoint 的「封裝總管」加入新功能時，會開啟功能設計工具。  
  
## 開啟功能設計工具  
 您可以使用功能設計工具，在功能中加入或移除 SharePoint 專案項目。  
  
#### 若要開啟功能設計工具  
  
1.  在 \[**方案總管**\] 中，展開 \[**功能**\]。  
  
2.  按兩下 *Feature1* 項目，或開啟 *Feature1* 項目的捷徑功能表，然後選擇 \[**檢視表設計工具**\]。  
  
## 檢視封裝的資訊清單檔  
 您可以使用功能設計工具來修改和產生功能的封裝資訊清單檔 \(feature.xml\)。  然後您可以在 Visual Studio 中檢視此檔案的 XML 程式碼。  
  
#### 若要檢視封裝的資訊清單檔  
  
1.  在 \[**功能設計工具**\] 中，選擇 \[**資訊清單**\] 索引標籤。  
  
#### 若要使用方案總管檢視封裝的資訊清單檔  
  
1.  在 \[**方案總管**\] 中，選擇 \[**顯示所有檔案**\] 圖示。  
  
2.  擴充功能、擴充 FeatureName、展開 FeatureName.feature，然後開啟 *FeatureName*.Template.xml 檔案。  
  
    > [!NOTE]  
    >  當您開啟功能範本資訊清單 XML 檔案時，檔案會自動進行驗證，而出現在 \[錯誤清單\] 視窗中的警告可以忽略。  
  
## 變更資訊清單範本  
 您可以在 Visual Studio \[XML 編輯器\] 或 \[資訊清單範本\] 窗格中變更功能資訊清單檔的 XML 程式碼。  對 XML 程式碼所做的任何變更會合併至功能的封裝資訊清單檔。  例如，您可能會想變更資訊清單範本來自訂功能屬性。  
  
#### 若要使用 XML 編輯器變更資訊清單範本  
  
1.  在 \[**功能設計工具**\] 中，選取 \[**資訊清單**\] 索引標籤，展開 \[**編譯選項**\] 節點，然後選擇 \[**在 XML 編輯器開啟**\] 連結。  
  
     對 XML 所做的變更會合併至封裝的資訊清單檔。  
  
#### 若要使用資訊清單範本窗格變更資訊清單範本  
  
1.  在 \[**功能設計工具**\] 中，選取 \[**資訊清單**\] 索引標籤，展開 \[**編譯選項**\] 節點，然後變更出現在資訊清單範本窗格中的 XML。  
  
     對 XML 所做的變更會出現在 \[**預覽封裝的資訊清單**\] 窗格中。  
  
## 覆寫封裝的資訊清單檔  
 您可以停用功能設計工具並手動建立 feature.xml 檔案。  第一次執行此程序時，功能設計工具中的目前設定會儲存至功能範本 XML 檔案。  然後您可以修改或覆寫 XML 程式碼。  
  
> [!NOTE]  
>  如果您在功能設計工具停用時在 XML 檔案中加入或移除 SharePoint 專案項目，這些專案項目不會封裝。  
  
#### 若要停用設計工具來覆寫封裝的資訊清單檔  
  
1.  在 \[**功能設計工具**\] 中，選擇 \[**資訊清單**\] 索引標籤。  
  
2.  展開 \[**編譯選項**\] 節點，選取 \[**覆寫產生的 XML 並在 XML 編輯器編輯資訊清單**\] 連結，然後選擇 \[**是**\] 按鈕。  
  
     範本便會以目前的封裝資訊清單檔更新。  
  
## 啟用功能設計工具  
 您可以重新啟用功能設計工具來自訂 feature.xml 檔案。  
  
#### 若要重新啟用設計工具  
  
1.  在 \[**功能設計工具**\] 中，選擇 \[**捨棄資訊清單編輯並重新啟用設計工具**\] 連結，然後選擇 \[**是**\] 按鈕。  
  
2.  範本便會以原始文字重新整理，對 XML 所做的任何變更會遺失。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  