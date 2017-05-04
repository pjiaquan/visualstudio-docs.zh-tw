---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  您可以建立自訂驗證規則來驗證 Visual Studio 所產生的方案套件。  您可以藉由從 \[**封裝總管**\] 中「封裝」或「功能」的內容功能表選取 \[**驗證**\]，對整個「功能」或「封裝」執行完整驗證。  當您將新的 SharePoint 專案項目或「功能」加入至專案來判斷「封裝」或「功能」是否為有效狀態時，會執行部分驗證。  
  
### 若要建立自訂的「封裝」驗證規則  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立會實作下列介面之一的類別：  
  
    -   若要建立「封裝」驗證規則，請實作 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 介面。  
  
    -   若要建立「功能」驗證規則，請實作 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 介面。  
  
4.  將 <xref:System.ComponentModel.Composition.ExportAttribute> 加入至類別。  此屬性可讓 Visual Studio 探索並載入您的驗證規則。  將 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 或 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 型別傳遞至屬性建構函式。  
  
## 範例  
 下列程式碼範例會示範如何建立自訂的「功能」驗證規則。  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint。  
  
-   System.ComponentModel.Composition。  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  