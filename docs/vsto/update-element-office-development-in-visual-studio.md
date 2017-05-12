---
title: "&lt;update&gt; 元素 (Visual Studio 中的 Office 程式開發)"
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
  - "update 項目"
  - "<update> 元素"
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<update> 元素"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &lt;update&gt; 元素 (Visual Studio 中的 Office 程式開發)
  `update` 項目會指定方案檢查更新的間隔。  
  
## 語法  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## 項目和屬性  
 `update` 項目是必要項，而且位於 `vstav3` 命名空間中。  
  
 `update` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要項。  請將下列其中一個值設定為啟用：<br /><br /> -   **true** 為檢查更新。<br />-   **false** 為避免檢查更新。|  
  
 `update` 項目具有下列子項目。  
  
### expiration  
 `expiration` 項目是必要項，而且位於 `vstav3` 命名空間中。  這個項目會指定方案檢查更新的間隔。  
  
 `expiration` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`maximumAge`|-   必要項。  將其設定為整數。|  
|`unit`|必要項。  請將 `unit` 設定為下列其中一個值：<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## 永遠檢查更新的範例  
  
### 描述  
 下列程式碼範例示範在 Office 方案中設定為永遠檢查更新的 `update` 項目。  
  
### 程式碼  
  
```  
<vstav3:update enabled="true" />  
```  
  
## 設定預設更新間隔的範例  
  
### 描述  
 下列程式碼範例示範 Office 方案應用程式資訊清單中的 `update` 項目。  這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中完整範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## 請參閱  
 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  