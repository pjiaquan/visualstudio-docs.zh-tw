---
title: "&lt;dependency&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<dependency> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 27
---
# &lt;dependency&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別要安裝的應用程式版本，以及應用程式資訊清單的位置。  
  
## 語法  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## 項目和屬性  
 `dependency` 項目為必要項。  它沒有屬性。  部署資訊清單可以具有多重 `dependency` 項目。  
  
 `dependency` 項目通常表示主應用程式對 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式內含組件的相依性。  如果您的 Main.exe 應用程式使用稱為 DotNetAssembly.dll 的組件，該組件就必須在相依性區段中列出。  然而，相依性也可能表示其他的相依性類型，像是對 Common Language Runtime 特定版本、全域組件快取 \(Global Assembly Cache，GAC\) 中的組件，或是 COM 物件的相依性。  由於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一種「不需接觸」的部署技術，因此無法起始這些相依性類型的下載和安裝，不過如果指定的一或多項相依性不存在，這種部署技術確實可以避免應用程式執行。  
  
## dependentAssembly  
 必要項。  這個項目包括了 `assemblyIdentity` 項目。  下表顯示 `dependentAssembly` 所支援的屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`preRequisite`|選擇項。  指定此組件應該已經存在於 GAC 之中。  有效值為 `true` 和 `false`。  如果為 `true`，而且指定的組件不存在於 GAC 之中，應用程式就無法執行。|  
|`visible`|選擇項。  識別最上層應用程式的識別 \(Identity\)，包括其相依性。  由 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 在內部使用以管理應用程式儲存和啟動。|  
|`dependencyType`|必要項。  這項相依性和應用程式之間的關係。  有效值為：<br /><br /> -   `install`。  代表和目前應用程式不同之安裝的元件。<br />-   `preRequisite`。  目前應用程式所需的元件。|  
|`codebase`|選擇項。  應用程式資訊清單的完整路徑。|  
|`size`|選擇項。  應用程式資訊清單大小 \(以位元組為單位\)。|  
  
## assemblyIdentity  
 必要項。  這個項目是 `dependentAssembly` 項目的子系。  `assemblyIdentity` 的內容必須和 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單中的描述相同。  下表顯示 `assemblyIdentity` 項目的屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  識別應用程式名稱。|  
|`Version`|必要項。  使用下列格式來指定應用程式的版本號碼：`major.minor.build.revision`|  
|`publicKeyToken`|必要項。  指定 16 個字元的十六進位字串，表示公開金鑰 \(Public Key\) 之 SHA\-1 雜湊的最後 8 個位元組，而應用程式或組件即是在該字串下簽署的。  用來簽章的公開金鑰必須有 2048 位元 \(含\) 以上。|  
|`processorArchitecture`|必要項。  指定微處理器。  對 32 位元 Windows 的有效值為 `x86`，對 64 位元 Windows 的有效值則為 `IA64`。|  
|`Language`|選擇項。  識別組件的兩部分語言代碼。  例如，EN\-US 代表英文 \(美國\)。  預設值為 `neutral`。  這個項目位於 `asmv2` 命名空間。|  
|`type`|選擇項。  為了和 Windows 並存安裝技術回溯相容，  唯一允許的值是 `win32`。|  
  
## hash  
 `hash` 項目是 `file` 項目的選擇性子項目。  `hash` 項目沒有任何屬性。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用應用程式中所有檔案的演算雜湊做為安全性檢查，以確定沒有檔案在部署後遭到變更。  如果沒有包含 `hash` 項目，則不會執行這項檢查。因此，建議您不要省略 `hash` 項目。  
  
## dsig:Transforms  
 `dsig:Transforms` 項目是 `hash` 項目的必要子系。  `dsig:Transforms` 項目沒有任何屬性。  
  
## dsig:Transform  
 `dsig:Transform` 項目是 `dsig:Transforms` 項目的必要子系。  下表顯示 `dsig:Transform` 事件的屬性：  
  
|屬性|描述|  
|--------|--------|  
|`Algorithm`|用來計算這個檔案的摘要演算法。  目前 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `urn:schemas-microsoft-com:HashTransforms.Identity`。|  
  
## dsig:DigestMethod  
 `dsig:DigestMethod` 項目是 `hash` 項目的必要子系。  下表顯示 `dsig:DigestMethod` 事件的屬性：  
  
|屬性|描述|  
|--------|--------|  
|`Algorithm`|用來計算這個檔案的摘要演算法。  目前 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 唯一使用的值是 `http://www.w3.org/2000/09/xmldsig#sha1`。|  
  
## dsig:DigestValue  
 `dsig:DigestValue` 項目是 `hash` 項目的必要子系。  `dsig:DigestValue` 項目沒有任何屬性。  它的值是指定檔案之計算的雜湊。  
  
## 備註  
 部署資訊清單通常有單一的 `assemblyIdentity` 項目，以識別應用程式的資訊清單版本名稱。  
  
## 範例  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單內的 `dependency` 項目。  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## 範例  
 下列程式碼範例對已經安裝在 GAC 中的組件指定相依性。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 範例  
 下列程式碼範例對 Common Language Runtime 的特定版本指定相依性。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 範例  
 下列程式碼範例指定作業系統相依性。  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> 項目](../deployment/dependency-element-clickonce-application.md)