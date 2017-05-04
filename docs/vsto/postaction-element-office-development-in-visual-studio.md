---
title: "&lt;postAction&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<postAction> 項目"
  - "<postAction> 項目"
  - "postAction 項目"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# &lt;postAction&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3`  命名空間的 `postAction`項目包含 `entrypoint` 項目和所有 `postActionData` 項目，這些項目與安裝 Office 方案後執行的部署後動作相關。  
  
## 語法  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## 項目和屬性  
 `postAction` 項目是選擇項，且位於 `vstav3`  命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postAction`項目。  
  
 `postAction`項目沒有任何屬性。  
  
 `postAction`具有下列項目。  
  
### entryPoint  
 選擇項。`vstav3`  命名空間中的 `entryPoint`項目角色會在 [&#60;entryPoints&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md) 中定義。  
  
### postActionData  
 選擇項。`vstav3`  命名空間中的 `postActionData`項目角色會在 [&#60;postActionData&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md) 中定義。  
  
## 部署後動作範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之 Office 解決方案的應用程式資訊清單中的 `postAction`項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  