---
title: "&lt;customizations&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "<customizations> 項目"
  - "customizations 項目"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<customizations> 項目"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;customizations&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4` 命名空間的 `customizations` 項目包含安裝及載入每個 Office 方案的所有資訊。  
  
## 文件層級自訂的語法  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## VSTO 增益集的語法  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## 項目和屬性  
 `customizations` 項目包含每個 Office 方案的特定資訊。 這個項目必須位於下列命名空間：`vstov4=urn:schemas-microsoft-com:vsto.v4`。 組件的子項目也必須在這個命名空間中。  
  
 `customizations` 項目沒有任何屬性。  
  
 `customizations` 項目具有下列子項目。  
  
### 自訂  
 必要項。`vstov4` 命名空間中的 `customization` 項目會在 [&#60;customization&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customization-element-office-development-in-visual-studio.md) 中定義。  
  
## 文件層級自訂的範例  
  
### 描述  
 下列程式碼範例說明文件層級自訂的 `customizations` 項目。  
  
> [!NOTE]  
>  這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## VSTO 增益集的範例  
  
### 描述  
 下列程式碼範例說明 VSTO 增益集的 `customizations` 項目。 這是包含表單區域的 Outlook VSTO 增益集。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  