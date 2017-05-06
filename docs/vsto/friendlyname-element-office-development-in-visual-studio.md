---
title: "&lt;friendlyName&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<friendlyName> 項目"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;friendlyName&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4`  命名空間的 `friendlyName` 項目會儲存已安裝的程式清單中顯示的名稱。  
  
## 語法  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## 項目和屬性  
 `friendlyName` 項目位於 `vstov4`  命名空間。 電腦上的已安裝程式清單和 Microsoft Office 應用程式的 \[COM VSTO 增益集\] 對話方塊中會顯示值。  
  
 `friendlyName` 項目沒有屬性或子項目。  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之應用程式層級方案中的 `friendlyName` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  