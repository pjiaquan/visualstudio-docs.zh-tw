---
title: "&lt;postActionData&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "<postActionData> 項目"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<postActionData> 項目"
  - "postActionData 項目"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActionData&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3`  命名空間的 `postActionData` 項目指定與安裝 Office 方案後所執行之任何部署後動作相關聯的資料。  
  
## 語法  
  
```  
<postActionData>  
</postActionData>  
```  
  
## 項目和屬性  
 `postActionData` 項目是選擇項，且位於 `vstav3`  命名空間。 在應用程式資訊清單中，會為每個部署後動作定義一個 `postActionData` 項目。  
  
 `postActions` 項目沒有任何屬性。  
  
 `postActions` 沒有任何子項目。  
  
## 部署後動作範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之 Office 方案的應用程式資訊清單中的 `postAction` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  