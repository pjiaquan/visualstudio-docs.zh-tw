---
title: "&lt;assembly&gt; 項目 (ClickOnce 應用程式) | Microsoft Docs"
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
  - "<assembly> 項目 [ClickOnce 應用程式資訊清單]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; 項目 (ClickOnce 應用程式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

應用程式資訊清單的最上層項目。  
  
## 語法  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## 項目和屬性  
 `assembly` 項目是根項目且是必要項，  它第一個包含的項目必須是 `assemblyIdentity` 項目。  資訊清單項目必須在下列其中一個命名空間中：  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 組件的子項目無論是以繼承還是標記的方式，也都必須同時存於這些命名空間中。  
  
 `assembly` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`manifestVersion`|必要項。  `manifestVersion` 屬性必須設定為 `1.0`。|  
  
## 範例  
 下列程式碼範例說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式之應用程式資訊清單中的 `assembly` 項目。  這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)中完整範例的一部分。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> 項目](../deployment/assembly-element-clickonce-deployment.md)