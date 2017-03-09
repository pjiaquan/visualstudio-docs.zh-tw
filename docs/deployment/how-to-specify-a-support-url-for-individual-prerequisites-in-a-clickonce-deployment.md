---
title: "如何：在 ClickOnce 部署中指定個別必要條件的支援 URL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "ClickOnce 部署, 必要條件"
  - "ClickOnce 部署, URL"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：在 ClickOnce 部署中指定個別必要條件的支援 URL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可以測試一些必須在用戶端電腦上具備的必要條件，以執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  這些必要條件包含 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的最小必要版本、作業系統的版本，以及必須在全域組件快取 \(GAC\) 中預先安裝的任何組件。  不過，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 無法自行安裝這些必要條件，因此若找不到某項必要條件，便會暫止安裝程序，並顯示一個對話方塊，說明安裝失敗的原因。  
  
 安裝必要條件的方式有兩種，  您可以使用啟動載入器 \(Bootstrapper\) 應用程式來安裝這些必要條件。  此外，您也可以為個別的必要條件指定支援 URL，如此便會在找不到必要條件時，透過對話方塊向使用者顯示支援 URL。  該 URL 參考的頁面可能包含安裝必要條件所需之指示的連結。  如果應用程式未針對個別的必要條件指定支援 URL，則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會顯示應用程式整體之部署資訊清單內指定的支援 URL \(若有定義的話\)。  
  
 雖然 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、Mage.exe 和 MageUI.exe 都可用來產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，但這些工具都未直接支援為個別必要條件指定支援 URL 的功能。  本文件將說明如何修改部署的應用程式資訊清單和部署資訊清單，使其包含這些支援 URL。  
  
### 為個別的必要條件指定支援 URL  
  
1.  在文字編輯器中，開啟 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的應用程式資訊清單 \(.manifest 檔\)。  
  
2.  針對作業系統的必要條件，將 `supportUrl` 屬性 \(Attribute\) 加入至 `dependentOS` 項目中：  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  對於某些 Common Language Runtime 版本的必要條件，將 `supportUrl` 屬性加入至指定 Common Language Runtime 相依性的 `dependentAssembly` 項目中：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  針對必須預先安裝在全域組件快取內之組件的必要條件，設定指定必要組件之 `dependentAssembly` 項目的 `supportUrl`：  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  選擇項。  針對以 .NET Framework 4 為目標的應用程式，在文字編輯器中開啟 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的部署資訊清單 \(.application 檔\)。  
  
6.  針對 .NET Framework 4 的必要條件，將 `supportUrl` 屬性加入至 `compatibleFrameworks` 項目中：  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  一旦手動變更了應用程式資訊清單，您就必須使用數位憑證重新簽署此應用程式資訊清單，然後更新部署資訊清單，並重新簽署部署資訊清單。  您必須使用 Mage.exe 或 MageUI.exe SDK 工具來完成這項工作，因為使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 重新產生這些檔案會清除手動變更的內容。  如需使用 Mage.exe 重新簽署資訊清單的詳細資訊，請參閱 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## .NET Framework 安全性  
 如果應用程式標記為在部分信任狀態下執行，此對話方塊中不會顯示支援 URL。  
  
## 請參閱  
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> 項目](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)