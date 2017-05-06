---
title: "&lt;postActions&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<postActions> 項目"
  - "postActions 項目"
  - "<postActions> 項目"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActions&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3`  命名空間的 `postActions` 項目包含描述安裝 Office 方案後所執行之部署後動作的所有 `postAction` 項目。  
  
## 語法  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## 項目和屬性  
 `postActions` 項目是選擇項，且位於 `vstav3`  命名空間。 在應用程式資訊清單中，只會定義一個 `postActions` 項目。  
  
 `postActions` 項目沒有任何屬性。  
  
 `postActions` 具有下列項目：  
  
### postAction  
 選擇項。`vstav3`  命名空間中的 `postAction` 項目角色會在 [&#60;postAction&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postaction-element-office-development-in-visual-studio.md) 中定義。  
  
## 部署後動作範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之 Office 方案的應用程式資訊清單中的 `postActions` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  