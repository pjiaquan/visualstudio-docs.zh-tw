---
title: "如何：使用封裝設計工具在套件中新增與移除功能 | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackageDesignerDesign"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 套件"
ms.assetid: 7dfa2c5d-3ac7-4573-abac-12a5e16efd1d
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用封裝設計工具在套件中新增與移除功能
  當您建立 SharePoint 方案時，Visual Studio 會將預設 SharePoint 功能加入至方案中的封裝。  在最後部署之前，您可以加入和移除 SharePoint 專案項目和功能，以修改 SharePoint 封裝。  
  
 除此之外，您還可以使用「封裝總管」加入和移除 SharePoint 專案項目。  您也可以檢視和變更放入封裝 \(.wsp\) 之 SharePoint 專案項目和功能的階層架構。  如需詳細資訊，請參閱[如何：使用封裝總管在套件中新增與移除功能和項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
## 將功能加入至 SharePoint 封裝  
 您可以使用「封裝設計工具」，將功能加入至 SharePoint 封裝。  
  
#### 若要使用封裝設計工具加入 SharePoint 功能  
  
1.  開啟 \[**封裝設計工具**\]。  
  
     如需詳細資訊，請參閱[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
2.  藉由執行下列一個或多個步驟，以加入一個或多個 SharePoint 功能：  
  
    1.  按兩下 \[**方案中的項目**\] 清單中您要加入的每個項目。  
  
    2.  選取您要加入的項目，然後選取 \[**加入**\] 按鈕 \(\>\)。  
  
    3.  選取 \[**全部加入**\] 按鈕 \(\>\>\) 立即加入所有項目。  
  
     例如，您可以按兩下 \[**方案中的項目**\] 清單中的項目，將它加入至 \[**套件中的項目**\] 清單。  
  
     SharePoint 專案項目和功能便會出現在 \[**套件中的項目**\] 清單中。  
  
## 從 SharePoint 封裝移除功能  
 您可以使用「封裝設計工具」，將功能從 SharePoint 封裝移除。  
  
#### 若要使用封裝設計工具移除 SharePoint 功能  
  
1.  在 \[**封裝中的項目**\] 清單中，選取您要移除的項目，然後選取 \[**移除**\] \(\<\) 按鈕或選取 \[**全部移除**\] 按鈕 \(\<\<\) 移除所有項目。  
  
     SharePoint 項目便會出現在 \[**方案中的項目**\] 清單中。  
  
## 請參閱  
 [建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)   
 [如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [NOT IN BUILD: How to: Modify Package Properties](http://msdn.microsoft.com/zh-tw/372089ce-cda9-4c21-beb2-f964990b96ee)   
 [How to: Create a Package](http://msdn.microsoft.com/zh-tw/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
  