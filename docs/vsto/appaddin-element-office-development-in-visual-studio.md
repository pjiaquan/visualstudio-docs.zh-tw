---
title: "&lt;appAddin&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]、<appAddin> 項目"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# &lt;appAddin&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4`  命名空間的 `appAddin` 項目會儲存自訂 VSTO 增益集特定的資訊。  
  
## 語法  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## 項目和屬性  
 `appAddin` 項目是必要的，且位於 `vstov4`  命名空間。 在應用程式資訊清單中，只可以定義一個 `appAddin` 項目。  
  
 `appAddin` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`application`|必要項。 識別 Microsoft Office 應用程式。 該值可以為下列其中一種：Excel、InfoPath、Outlook、PowerPoint、Project、Visio 或 Word。|  
|`loadBehavior`|選擇項。 根據預設，將此值設定為下列值時，會啟用 `loadBehavior`。 若要進行偵錯，可以將此值設定為 2 來停用 VSTO 增益集。 如需詳細資訊，請參閱 [VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md) 中標題為 LoadBehavior 值的表格。|  
|`keyName`|必要項。 這個值是該應用程式載入 VSTO 增益集時將要使用的登錄機碼名稱。 如需詳細資訊，請參閱[VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。|  
  
 `appAddin` 項目具有下列子項目。  
  
### friendlyName  
 選擇項。[&#60;friendlyName&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md) 中會說明 `friendlyName` 項目。  
  
### 說明  
 選擇項。[&#60;description&#62; 元素 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/description-element-office-development-in-visual-studio.md) 中會說明 `description` 項目。  
  
### formRegions  
 只有包含表單區域的 Outlook VSTO 增益集需要。[&#60;formRegions&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregions-element-office-development-in-visual-studio.md) 中會說明 `formRegions` 項目。  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之 Outlook 方案中的 `appAddin` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  