---
title: "&lt;應用程式&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]、<應用程式> 項目"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt;應用程式&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3` 命名空間的 `application` 項目會包裝 Office 方案的描述。 文件層級自訂與 VSTO 增益集的子項目不同。  
  
## 文件層級自訂的語法  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## 應用程式層級增益集的語法  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## 項目和屬性  
 `vstav3` 命名空間的 `application` 項目是包裝 `vstov4` 命名空間所包含之所有自訂特定資訊的節點。  
  
 `application` 項目沒有任何屬性。  
  
 `application` 項目具有下列項目。  
  
### 自訂  
 `vstov3` 命名空間中的 `customization` 項目角色會在 [&#60;customization&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customization-element-office-development-in-visual-studio.md) 中定義。  
  
## 文件層級自訂範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之文件層級 Office 方案中的 `application` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之完整範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之應用程式層級 Office 方案中的 `application` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之完整範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  