---
title: "&lt;assemblyIdentity&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "<assemblyIdentity> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的主要組件。  
  
## 語法  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## 項目和屬性  
 `assemblyIdentity` 項目為必要項。  它不包含子項目而且具有下列屬性：  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要項。  識別部署的人們可讀取的 \(Human\-Readable\) 名稱以做為資訊提供之用。<br /><br /> 如果 `name` 包含特殊字元 \(例如單引號或雙引號\)，則應用程式可能會無法啟動。|  
|`version`|必要項。  以下列格式指定組件的版本號碼：`major.minor.build.revision`。<br /><br /> 這個值必須在更新的資訊清單中遞增才能觸發應用程式更新。|  
|`publicKeyToken`|必要項。  指定 16 字元的十六進位字串，其表示公開金鑰 \(Public Key\) 之 SHA\-1 雜湊值 \(Hash Value\) 的最後 8 個位元組，而部署資訊清單即是在該字串下簽署的。  用來進行簽章的公開金鑰必須有 2048 位元 \(含\) 以上。<br /><br /> 雖然簽署組件是建議但選擇性的作業，但此屬性為必要項。  如果組件未簽署，您應從自我簽署組件複製值或使用全為零的「空」值。|  
|`processorArchitecture`|必要項。  指定處理器。  有效值如下：`msil` 適用於所有處理器；`x86` 適用於 32 位元 Windows；`IA64` 適用於 64 位元 Windows；以及 `Itanium` 適用於 Intel 64 位元 Itanium 處理器。|  
|`type`|必要項。  為了和 Windows 並存安裝技術相容，  唯一允許的值是 `win32`。|  
  
## 備註  
  
## 範例  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的 `assemblyIdentity` 項目。  這個程式碼範例是 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)主題完整範例的一部分。  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> 項目](../deployment/assemblyidentity-element-clickonce-application.md)