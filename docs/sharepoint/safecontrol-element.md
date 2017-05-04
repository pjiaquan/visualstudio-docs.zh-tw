---
title: "SafeControl Element | Microsoft Docs"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  表示為了讓任何使用者可存取 SharePoint 網站上的任何 ASPX 頁面而指定為安全的 ASPX 控制項或 Web 組件。  
  
## 語法  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**Assembly**|選擇性 **xs:string** 屬性。<br /><br /> 組件的名稱，ASPX 控制項或網頁組件的名稱是在這個組件中定義的。  預設情況下，這個屬性會使用 **$SharePoint.Project.AssemblyFullName$** 可取代參數做為組件名稱。  如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。|  
|**IsSafe**|選擇性 **xs:boolean** 屬性。<br /><br /> 指定不受信任的使用者能否安全存取 ASPX 控制項或網頁組件。|  
|**IsSafeAgainstScript**|選擇性 **xs:boolean** 屬性。<br /><br /> 指定不受信任的使用者能否檢視或編輯 ASPX 控制項或網頁組件的屬性。|  
|**Name**|選擇性 **xs:string** 屬性。<br /><br /> 集合中這個安全控制項項目的名稱。|  
|**Namespace**|選擇性 **xs:string** 屬性。<br /><br /> ASPX 控制項或網頁組件的命名空間。|  
|**TypeName**|選擇性 **xs:string** 屬性。<br /><br /> ASPX 控制項或網頁組件的型別名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示為了讓任何使用者可存取 SharePoint 網站上的任何 ASPX 頁面而指定為安全的 ASPX 控制項和 Web 組件集合。|  
  
## 備註  
 如需安全控制項的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
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
  
  