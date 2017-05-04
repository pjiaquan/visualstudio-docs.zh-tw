---
title: "SharePoint Project Item Schema Reference | Microsoft Docs"
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
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio 會使用 SharePoint 專案項目結構描述來驗證 .spdata 檔案的內容。  .spdata 檔案會指定 SharePoint 專案項目的內容和行為。  如需 SharePoint 專案項目內容的詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 SharePoint 專案項目結構描述的名稱為 ProjectItemModelSchema.xsd，且會根據預設安裝在 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas 中。  
  
 根項目為 [ProjectItem](../sharepoint/projectitem-element.md) 項目。  下表會說明結構描述定義的所有項目。  
  
|元素|描述|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|表示與 SharePoint 專案項目關聯之自訂資料項目的集合。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|表示與 SharePoint 專案項目關聯且格式為索引鍵\/值的自訂資料項目。  索引鍵和值都必須是字串。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示將「功能」部署至 SharePoint 時「功能」中所含屬性值的集合。  部署「功能」之後，您可以存取程式碼中的屬性值。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|表示將「功能」部署至 SharePoint 時「功能」中所含的自訂屬性。  部署「功能」之後，您可以存取程式碼中的屬性。|  
|[檔案](../sharepoint/files-element.md)|指定要隨同 SharePoint 專案項目部署的檔案，例如，「功能」項目檔案或專案的輸出。|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案項目。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|表示將專案項目部署至 SharePoint 時專案項目中所含的 SharePoint 檔案，例如「功能」項目檔案。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|表示對應資料夾。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|表示將專案項目部署至 SharePoint 時專案項目中所含的專案輸出。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|表示為了讓任何使用者可存取 SharePoint 網站上的任何 ASPX 頁面而指定為安全的 ASPX 控制項或 Web 組件。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示為了讓任何使用者可存取 SharePoint 網站上的任何 ASPX 頁面而指定為安全的 ASPX 控制項和 Web 組件集合。|  
  
## 請參閱  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  