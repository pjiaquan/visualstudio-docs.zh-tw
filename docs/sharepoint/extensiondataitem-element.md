---
title: "ExtensionDataItem Element"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  表示與 SharePoint 專案項目關聯且格式為索引鍵\/值的自訂資料項目。  索引鍵和值都必須是字串。  
  
## 語法  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**Key**|必要的 **xs:string** 屬性。<br /><br /> 用來儲存及擷取資料項目的索引鍵。|  
|**Value**|必要的 **xs:string** 屬性。<br /><br /> 資料項目的值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|表示與 SharePoint 專案項目關聯之自訂資料項目的集合。|  
  
## 備註  
 當您使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性將自訂資料與 SharePoint 專案項目產生關聯時，Visual Studio 會將資料儲存至專案項目之 .spdata 檔案中的新 **ExtensionDataItem** 項目。  如需詳細資訊，請參閱[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  