---
title: "&lt;document&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "document 項目"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]、<document> 項目"
  - "<document> 項目"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;document&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstov4` 命名空間的 `document` 項目會儲存文件層級自訂的自訂特定資訊。  
  
## 語法  
  
```  
<document solutionId />  
```  
  
## 項目和屬性  
 文件層級自訂才需要。  `document` 項目位於 `vstov4` 命名空間。  `document` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`solutionId`|必要項。  Visual Studio工具使用 Office 的執行階段的唯一識別文件層級解決方案的 GUID。  這個值會儲存為 \_AssemblyLocation 自訂文件屬性。  如需詳細資訊，請參閱[自訂文件屬性概觀](../vsto/custom-document-properties-overview.md)。|  
  
 `document` 沒有子項目。  
  
## 文件層級自訂範例  
  
### 描述  
 在下列程式碼範例中，會示範使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之文件層級 Office 方案中的 `document` 項目。  這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中完整範例的一部分。  
  
### 程式碼  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  