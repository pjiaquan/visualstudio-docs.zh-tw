---
title: "Files Element"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  指定要以 SharePoint 專案項目部署的檔案，例如 Feature 項目檔案，以及相依非 SharePoint 專案的輸出檔案。  
  
## 語法  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## 類型  
 **FileCollectionType**  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|選擇性 **ProjectItemFileType** 項目。<br /><br /> 表示將專案項目部署至 SharePoint 時專案項目中所含的 SharePoint 檔案，例如「功能」項目檔案。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|選擇性 **ProjectOutputFileType** 項目。<br /><br /> 表示將專案項目部署至 SharePoint 時專案項目中所含的專案輸出。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案項目。  這是 .spdata 檔案必要的根項目。|  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  