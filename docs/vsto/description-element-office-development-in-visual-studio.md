---
title: "&lt;description&gt; 元素 (Visual Studio 中的 Office 程式開發)"
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
  - "description 項目"
  - "<description> 元素"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<description> 元素"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;description&gt; 元素 (Visual Studio 中的 Office 程式開發)
  `vstov4`  命名空間的 `description` 元素會儲存 Microsoft Office 應用程式之 \[COM 增益集\] 對話方塊中所顯示的 Office 解決方案描述。  
  
## 語法  
  
```  
<description>  
</description>  
```  
  
## 項目和屬性  
 選擇項。`description` 元素位於 `vstov4`  命名空間。 它包含 Microsoft Office 應用程式之 \[COM 增益集\] 對話方塊中所顯示的增益集描述。  
  
 `description` 元素沒有屬性或元素。  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之應用程式層級解決方案的 `description` 元素。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  