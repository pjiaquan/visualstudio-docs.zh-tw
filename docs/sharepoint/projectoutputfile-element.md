---
title: "ProjectOutputFile Element"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  表示將專案項目部署至 SharePoint 時專案項目中所含的個別專案輸出。  
  
## 語法  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## 類型  
 **ProjectOutputFileType**  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**ProjectId**|必要的 **xs:string** 屬性。<br /><br /> 具有您要包含之輸出的相依專案的 GUID。  這會對應至相依專案檔中的 **ProjectGuid** 項目。|  
|**ProjectPath**|必要的 **xs:string** 屬性。<br /><br /> 具有您要包含之輸出的相依專案的相對路徑 \(包含專案檔案名稱\)。  此路徑相對於 SharePoint 專案的根資料夾，此 SharePoint 專案包含 SharePoint 專案項目。|  
|**Target**|選擇性 **xs:string** 屬性。<br /><br /> 相依專案輸出將部署於 SharePoint 伺服器的路徑，相對於部署根資料夾路徑。  **Type** 屬性所指定的部署類型會決定部署根資料夾。<br /><br /> 如需詳細資訊，請參閱 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md) 中 SharePoint 專案項目之 **Deployment Path** 和 **Deployment Root** 屬性的描述。|  
|**Type**|必要的 **xs:string** 屬性。<br /><br /> 相依專案輸出所用的部署型別。  如需可能的値的詳細資訊，請參閱 SharePoint 專案項目的 **Deployment Type** 屬性 \(在[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)中\)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[檔案](../sharepoint/files-element.md)|指定將 SharePoint 專案項目部署至 SharePoint 時，專案項目中所含的檔案。|  
  
## 備註  
 使用 **ProjectOutputFile** 項目包含 SharePoint 專案項目部署中的專案的輸出。  您可以指定不同的專案，也可以指定包含專案項目的同一個專案。  如需詳細資訊，請參閱 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  