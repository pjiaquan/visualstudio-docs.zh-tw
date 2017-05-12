---
title: "&lt;formRegions&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "formRegions 項目"
  - "<formRegions> 項目"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<formRegions> 項目"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;formRegions&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4`  命名空間的 `formRegions` 項目包含與 VSTO 增益集相關聯的 Microsoft Office Outlook 表單區域。  
  
## 語法  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## 項目和屬性  
 `vstov4`  命名空間的 `formRegions` 項目包含 Outlook VSTO 增益集的所有 `formRegion` 項目。 此項目只有包含表單區域的 Outlook VSTO 增益集需要。  
  
 在應用程式資訊清單中，只可以定義一個 `formRegions` 項目。  
  
 `formRegions` 項目沒有任何屬性。  
  
 `formRegions` 項目具有下列項目。  
  
### formRegion  
 包含表單區域的 Outlook VSTO 增益集需要。`formRegion` 項目會定義在 [&#60;formRegion&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregion-element-office-development-in-visual-studio.md) 中。  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之應用程式層級 Office 方案的應用程式資訊清單中的 `formRegions` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  