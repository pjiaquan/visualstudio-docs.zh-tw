---
title: "FeatureProperty Element | Microsoft Docs"
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
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  表示將「功能」部署至 SharePoint 時「功能」中所含的自訂屬性。  部署「功能」之後，您可以存取程式碼中的屬性。  
  
## 語法  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**Key**|必要的 **xs:string** 屬性。<br /><br /> 用來儲存和擷取屬性值的索引鍵。  每個屬性必須具有一個索引鍵，此索引鍵在功能內必須是唯一的。|  
|**Value**|必要的 **xs:string** 屬性。<br /><br /> 屬性值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示將「功能」部署至 SharePoint 時「功能」中所含屬性值的集合。|  
  
## 備註  
 如需 Feature 屬性的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
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
  
  