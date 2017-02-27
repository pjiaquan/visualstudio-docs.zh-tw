---
title: "&lt;assembly&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;assembly&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

部署資訊清單的最上層項目。  
  
## 語法  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## 項目和屬性  
 `assembly` 項目是根項目且是必要項，  它第一個包含的項目必須是 `assemblyIdentity` 項目。  資訊清單項目必須在下列命名空間內：`urn:schemas-microsoft-com:asm.v1`、`urn:schemas-microsoft-com:asm.v2` 和 `http://www.w3.org/2000/09/xmldsig#`。  組件的子項目無論是以繼承還是標記的方式，也都必須同時存於這些命名空間中。  
  
 `assembly` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`manifestVersion`|必要項。  這個屬性必須設定為 `1.0`。|  
  
## 範例  
 在下列程式碼範例中，說明了使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 進行部署的應用程式之部署資訊清單中的 `assembly` 項目。  這個程式碼範例是 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題完整範例的一部分。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> 項目](../deployment/assembly-element-clickonce-application.md)