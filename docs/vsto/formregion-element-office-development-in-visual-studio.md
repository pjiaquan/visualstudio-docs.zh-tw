---
title: "&lt;formRegion&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<formRegion> 項目"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;formRegion&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4`  命名空間的 `formRegion` 項目會識別與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。  
  
## 語法  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## 項目和屬性  
 `vstov4`  命名空間的 `formRegion` 項目會識別與 Outlook VSTO 增益集相關聯的表單區域。 只有包含表單區域的 Outlook VSTO 增益集才需要這個項目。  
  
 單一 VSTO 增益集的 `formRegions` 項目中可以定義多個 `formRegion` 項目。  
  
 `formRegion` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要項。 識別表單區域名稱。|  
  
 `formRegion` 項目具有下列子項目。  
  
### messageClass  
 `messageClass`  項目會識別與表單區域相關聯的 Outlook 表單。  
  
 `messageClass` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要項。 識別與表單區域相關聯的表單。|  
  
## 範例  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之 Outlook VSTO 增益集的應用程式資訊清單中的 `formRegion` 項目。 有三個訊息類別與這個表單區域相關聯。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## 請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  