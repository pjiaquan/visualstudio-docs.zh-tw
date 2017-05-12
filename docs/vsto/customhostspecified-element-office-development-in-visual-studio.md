---
title: "&lt;customHostSpecified&gt; 元素 (Visual Studio 中的 Office 程式開發)"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<customHostSpecified> 元素"
  - "<customHostSpecified> 元素"
  - "customHostSpecified 項目"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customHostSpecified&gt; 元素 (Visual Studio 中的 Office 程式開發)
  `customHostSpecified` 項目表示這個方案不是獨立的應用程式。  Office 方案包含 Microsoft Office 應用程式中所裝載的元件。  
  
## 語法  
  
```  
<customHostSpecified />  
```  
  
## 項目和屬性  
 Office 方案需要 `customHostSpecified` 項目。  這個項目是在 `co.v1` 命名空間中，指出這個部署包含了將部署於自訂主機內的元件，而且不是獨立的應用程式。  
  
 這個項目是應用程式資訊清單中第一個 `<entrypoint>` 項目的子系。  在 `<entrypoint>` 項目或 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 中可能沒有其他子項目會在安裝期間引發驗證錯誤。  
  
 這個項目沒有任何屬性和子項目。  
  
## 範例  
 下列程式碼範例會說明`customHostSpecified`應用程式資訊清單在 Office解決方案中的項目。   這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中完整範例的一部分。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  