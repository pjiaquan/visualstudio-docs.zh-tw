---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  表示將專案項目部署至 SharePoint 時專案項目中所含的 SharePoint 檔案，例如「功能」項目檔案。  
  
## 語法  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## 類型  
 **ProjectItemFileType**  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**Source**|必要的 **xs:string** 屬性。<br /><br /> 與專案項目一起部署之檔案的名稱。|  
|**Target**|選擇性 **xs:string** 屬性。<br /><br /> 檔案將部署於 SharePoint 上的路徑，相對於部署根資料夾。  **Type** 屬性所指定的部署類型會決定部署根資料夾。  如果沒有指定 **Target** 屬性，就會以 **Source** 屬性中指定的名稱將檔案部署至資料夾中。<br /><br /> 如需詳細資訊，請參閱 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md) 中 SharePoint 專案項目之 **Deployment Path** 和 **Deployment Root** 屬性的描述。|  
|**Type**|必要的 **xs:string** 屬性。<br /><br /> 檔案之部署的型別。  如需可能的値的詳細資訊，請參閱 SharePoint 專案項目的 **Deployment Type** 屬性 \(在[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)中\)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[檔案](../sharepoint/files-element.md)|指定將 SharePoint 專案項目部署至 SharePoint 時，專案項目中所含的檔案。|  
  
## 備註  
 **ProjectItemFile** 元素中通常參考的 SharePoint 檔案包括功能項目檔案 \(Elements.xml\)、清單定義 \(Schema.xml\) 的結構描述檔和網頁組件 \(.webpart\) 的網頁組件定義檔。  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  