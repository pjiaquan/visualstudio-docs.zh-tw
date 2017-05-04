---
title: "&lt;customization&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<customization> 項目"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customization&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4` 命名空間的 `customization`項目描述特定的 Office 方案。 文件層級自訂與 VSTO 增益集的子項目不同。  
  
## 文件層級自訂的語法  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## VSTO 增益集的語法  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## 項目和屬性  
 `customization`項目包含自訂的特定資訊。 此項目必須位於下列命名空間中：`vstov4=urn:schemas-microsoft-com:vsto.v4`。 每個 Office 方案都有一個 `customization`項目。 例如，如果您在多專案的部署中部署三個 Office 方案，則在應用程式資訊清單中會有三個 `customization`項目。  
  
 組件的子項目也必須在此命名空間中。  
  
 `customization`項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`id`|多專案部署所需。`id`項目能唯一地識別 Office 方案。|  
  
### 文件層級自訂  
 `customization`項目具有下列子項目。  
  
#### 文件  
 `vstov4` 命名空間中的 `document`項目會在 [&#60;document&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/document-element-office-development-in-visual-studio.md) 中定義。  
  
### VSTO 增益集  
 `customization`項目具有下列子項目。  
  
#### appAddin  
 `vstov4` 命名空間中的 `appAddin`項目會在 [&#60;appAddin&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md) 中定義。  
  
## 文件層級自訂的範例  
  
### 描述  
 下列程式碼範例可說明文件層級自訂的 `customization`項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## VSTO 增益集的範例  
  
### 描述  
 下列程式碼範例說明 VSTO 增益集的 `customization`項目。 這是包含表單區域的 Outlook VSTO 增益集。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  