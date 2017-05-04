---
title: "ProjectItemFolder Element | Microsoft Docs"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  表示對應資料夾。  
  
## 語法  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## 類型  
 **ProjectItemFolderType**  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**Target**|必要的 **xs:string** 屬性。<br /><br /> SharePoint 安裝中資料夾的路徑 \(對應資料夾所對應的路徑\) 相對於部署根資料夾。  **Type** 屬性所指定的部署類型會決定部署根資料夾。<br /><br /> 如需詳細資訊，請參閱 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md) 中 SharePoint 專案項目之 **Deployment Path** 和 **Deployment Root** 屬性的描述。|  
|**Type**|必要的 **xs:string** 屬性。<br /><br /> 對應資料夾之部署的型別。  如需可能的値的詳細資訊，請參閱 SharePoint 專案項目的 **Deployment Type** 屬性 \(在[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)中\)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案項目。  這是 .spdata 檔案必要的根項目。|  
  
## 備註  
 如需對應資料夾的詳細資訊，請參閱 [如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  