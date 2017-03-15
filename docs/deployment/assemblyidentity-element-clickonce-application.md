---
title: "&lt;assemblyIdentity&gt; 項目 (ClickOnce 應用程式) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> 項目 [ClickOnce 應用程式資訊清單]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# &lt;assemblyIdentity&gt; 項目 (ClickOnce 應用程式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署中部署的應用程式。  
  
## 語法  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## 項目和屬性  
 `assemblyIdentity` 項目為必要項。  它不包含子項目而且具有下列屬性：  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  識別應用程式名稱。<br /><br /> 如果 `Name` 包含特殊字元 \(例如單引號或雙引號\)，則應用程式可能會無法啟動。|  
|`Version`|必要項。  使用下列格式來指定應用程式的版本號碼：`major.minor.build.revision`|  
|`publicKeyToken`|選擇項。  指定 16 字元十六進位字串，其表示公開金鑰 \(Public Key\) 之 `SHA-1` 雜湊值 \(Hash Value\) 的最後 8 個位元組，而應用程式或組件即是在該字串下簽署的。  用來對資料庫目錄 \(Catalog\) 進行簽章的公開金鑰必須有 2048 位元 \(含\) 以上。<br /><br /> 雖然簽署組件是建議但選擇性的作業，但此屬性為必要項。  如果組件未簽署，您應從自我簽署組件複製值或使用全為零的「空」值。|  
|`processorArchitecture`|必要項。  指定處理器。  有效值如下：`msil` 適用於所有處理器；`x86` 適用於 32 位元 Windows；`IA64` 適用於 64 位元 Windows；以及 `Itanium` 適用於 Intel 64 位元 Itanium 處理器。|  
|`language`|必要項。  識別組件的兩部分語言程式碼 \(例如，`en-US`\)，  這個項目位於 `asmv2` 命名空間。  如果未指定，則預設值為 `neutral`。|  
  
## 範例  
  
### 描述  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中的 `assemblyIdentity` 項目。  這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)中完整範例的一部分。  
  
### 程式碼  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> 項目](../deployment/assemblyidentity-element-clickonce-deployment.md)