---
title: "&lt;vstoRuntime&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<vstoRuntime> 項目"
  - "<vstoRuntime> 項目"
  - "vstoRuntime 項目"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# &lt;vstoRuntime&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3`  命名空間的 `vstoRuntime` 項目包含特定 Office 方案支援的 Visual Studio Tools for Office Runtime 版本。  
  
## 語法  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## 項目和屬性  
 `vstoRuntime` 項目是必要項，且位於 `vstav3`  命名空間。 如果 Office 方案支援兩種 Visual Studio Tools for Office Runtime 版本，應用程式資訊清單中會有兩個 `vstoRuntime` 項目。  
  
 `vstoRuntime` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`release`|必要項。 Visual Studio Tools for Office Runtime 的發行版本。|  
|`version`|必要項。 Visual Studio Tools for Office Runtime 的版本號碼。|  
|`supportUrl`|選擇項。 Visual Studio Tools for Office Runtime 的安裝位置連結。|  
  
 `vstoRuntime` 沒有任何項目。  
  
## 範例  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之 Office 方案的應用程式資訊清單中的 `vstoRuntime` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  