---
title: "&lt;customErrorReporting&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;customErrorReporting&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定要在錯誤發生時顯示的 URI。  
  
## 語法  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## 備註  
 這是選擇性項目。  若未指定此項目，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會顯示錯誤對話方塊，說明例外狀況 \(Exception\) 堆疊。  如果有 `customErrorReporting` 項目，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會顯示 `uri` 參數指定的 URI。  目標 URI 將包含外部例外狀況類別、內部例外狀況類別以及內部例外狀況訊息做為參數。  
  
 使用此項目，可以將錯誤報告功能加入至您的應用程式。  由於產生的 URI 包含錯誤類型的相關資訊，因此您的網站可以剖析該資訊，並顯示適當的疑難排解畫面等等。  
  
## 範例  
 下列程式碼片段說明 `customErrorReporting` 項目以及它可能產生的 URI。  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)