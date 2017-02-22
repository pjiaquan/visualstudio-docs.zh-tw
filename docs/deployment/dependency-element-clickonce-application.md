---
title: "&lt;dependency&gt; 項目 (ClickOnce 應用程式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> 項目 [ClickOnce 應用程式資訊清單]"
  - "資料清單 [ClickOnce], dependency 項目"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; 項目 (ClickOnce 應用程式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別應用程式所需的平台或組件相依性。  
  
## 語法  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## 項目和屬性  
 `dependency` 項目為必要項。  相同的應用程式資訊清單內可能會有多個 `dependency` 的執行個體。  
  
 `dependency` 項目沒有屬性 \(Attribute\)，而且會包含下列子項目。  
  
### dependentOS  
 選擇項。  包含 `osVersionInfo` 項目。  `dependentOS` 和 `dependentAssembly` 項目是互斥的 \(Mutually Exclusive\)：兩者之一必須為 `dependency` 項目存在，不過兩者無法並存。  
  
 `dependentOS` 支援下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`supportUrl`|選擇項。  指定相依平台的支援 URL。  如果找到必要的平台，便會對使用者顯示此 URL。|  
|`description`|選擇項。  以人們可讀的 \(Human\-Readable\) 格式，描述由 `dependentOS` 項目所描述的作業系統。|  
  
### osVersionInfo  
 必要項。  這個項目是 `dependentOS` 項目的子系，並含有 `os` 項目。  此項目沒有任何屬性。  
  
### os  
 必要項。  這個項目是 `osVersionInfo` 項目的子系。  此項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`majorVersion`|必要項。  指定 OS 的主要版本號碼。|  
|`minorVersion`|必要項。  指定 OS 的次要版本號碼。|  
|`buildNumber`|必要項。  指定 OS 的組建編號。|  
|`servicePackMajor`|必要項。  指定 OS 的 Service Pack 主要號碼。|  
|`servicePackMinor`|選擇項。  指定 OS 的 Service Pack 次要號碼。|  
|`productType`|選擇項。  識別產品類型值。  有效值為 `server`、`workstation` 和 `domainController`。  例如，對於 Windows 2000 Professional，此屬性值為 `workstation`。|  
|`suiteType`|選擇項。  識別系統上可用的產品套件，或是系統的組態型別。  有效值為 `backoffice`、`blade`、`datacenter`、`enterprise`、`home`、`professional`、`smallbusiness`、`smallbusinessRestricted` 和 `terminal`。  例如，對於 Windows 2000 Professional，此屬性值為 `professional`。|  
  
### dependentAssembly  
 選擇項。  包含 `assemblyIdentity` 項目。  `dependentOS` 和 `dependentAssembly` 項目是互斥的 \(Mutually Exclusive\)：兩者之一必須為 `dependency` 項目存在，不過兩者無法並存。  
  
 `dependentAssembly` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`dependencyType`|必要項。  指定相依性類型。  有效值為 `preprequisite` 和 `install`。  `install` 組件已安裝為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的一部分。  全域組件快取 \(GAC\) 中必須有 `prerequisite` 組件，才能安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。|  
|`allowDelayedBinding`|必要項。  指定是否可以用程式設計的方式在執行階段載入組件。|  
|`group`|選擇項。  如果 `dependencyType` 屬性設為 `install`，則會指定只有視需要才安裝的組件具名群組。  如需詳細資訊，請參閱 [逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md)。<br /><br /> 如果此屬性設為 `framework`，而 `dependencyType` 屬性設為 `prerequisite`，則會將組件指定為 .NET Framework 的一部分。  在 [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 上安裝組件時，不會檢查全域組件快取 \(GAC\) 中是否有此組件。|  
|`codeBase`|當 `dependencyType` 屬性設為 `install` 時，這是必要項。  相依組件的路徑，  可以是絕對路徑，或是相對於資訊清單程式碼基底 \(Code Base\) 的路徑。  為了讓組件資訊清單生效，這個路徑必須是有效的 URI。|  
|`size`|當 `dependencyType` 屬性設為 `install` 時，這是必要項。  相依組件的大小，以位元組為單位。|  
  
### assemblyIdentity  
 必要項。  這個項目是 `dependentAssembly` 項目的子系，並具備下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要項。  識別應用程式名稱。|  
|`version`|必要項。  使用下列格式來指定應用程式的版本號碼：`major.minor.build.revision`|  
|`publicKeyToken`|選擇項。  指定 16 字元十六進位字串，其表示公開金鑰 \(Public Key\) 之 `SHA-1` 雜湊值 \(Hash Value\) 的最後 8 個位元組，而應用程式或組件即是在該字串下簽署的。  用來對資料目錄進行簽章的公開金鑰 \(Public Key\) 必須有 2048 位元 \(含\) 以上。|  
|`processorArchitecture`|選擇項。  指定處理器。  對 32 位元 Windows 的有效值為 `x86`，對 64 位元 Windows 的有效值則為 `I64`。|  
|`language`|選擇項。  識別組件的兩部分語言代碼 \(例如，EN\-US\)。|  
  
### hash  
 `hash` 項目是 `assemblyIdentity` 項目的選擇性子項目。  `hash` 項目沒有任何屬性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用應用程式中所有檔案的演算雜湊做為安全性檢查，以確定沒有檔案在部署後遭到變更。  如果沒有包含 `hash` 項目，則不會執行這項檢查。因此，建議您不要省略 `hash` 項目。  
  
### dsig:Transforms  
 `dsig:Transforms` 項目是 `hash` 項目的必要子系。  `dsig:Transforms` 項目沒有任何屬性。  
  
### dsig:Transform  
 `dsig:Transform` 項目是 `dsig:Transforms` 項目的必要子系。  `dsig:Transform` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Algorithm`|用來計算這個檔案的摘要演算法。  目前 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
### dsig:DigestMethod  
 `dsig:DigestMethod` 項目是 `hash` 項目的必要子系。  `dsig:DigestMethod` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Algorithm`|用來計算這個檔案的摘要演算法。  目前 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
### dsig:DigestValue  
 `dsig:DigestValue` 項目是 `hash` 項目的必要子系。  `dsig:DigestValue` 項目沒有任何屬性。  它的值是指定檔案之計算的雜湊。  
  
## 備註  
 您的應用程式所用的所有組件必須有對應的 `dependency` 項目。  相依組件不包含必須預先安裝在全域組件快取中，做為平台組件的組件。  
  
## 範例  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中的 `dependency` 項目。  這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)主題完整範例的一部分。  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> 項目](../deployment/dependency-element-clickonce-deployment.md)