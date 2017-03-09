---
title: "如何：使用 ClickOnce 來部署可在多個 .NET Framework 版本上執行的應用程式 | Microsoft Docs"
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
  - "ClickOnce 應用程式, 多個 .NET Framework 版本"
  - "ClickOnce 部署, 多個 .NET Framework 版本"
  - "部署應用程式 [ClickOnce], 多個 .NET Framework 版本"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用 ClickOnce 來部署可在多個 .NET Framework 版本上執行的應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 ClickOnce 部署技術，部署以多個 .NET Framework 版本為目標的應用程式。  您必須產生及更新應用程式和部署資訊清單。  
  
> [!NOTE]
>  您應該先確認應用程式可搭配多個 .NET Framework 版本執行，然後再將應用程式變更為以多個 .NET Framework 版本為目標。   [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 相對於 .NET Framework 2.0、.NET Framework 3.0 與 .NET Framework 3.5，包含不同版本的 Common Language Runtime。  
  
 這個程序需要下列步驟：  
  
1.  產生應用程式和部署資訊清單。  
  
2.  變更部署資訊清單以列出多個 .NET Framework 版本。  
  
3.  變更 app.config 檔案以列出相容的 .NET Framework 執行階段版本。  
  
4.  變更應用程式資訊清單，將相依組件標示為 .NET Framework 組件。  
  
5.  簽署應用程式資訊清單。  
  
6.  更新及簽署部署資訊清單。  
  
### 若要產生應用程式和部署資訊清單  
  
-   使用 \[發行精靈\] 或 \[專案設計工具\] 的 \[發行頁\]，發行應用程式以及產生應用程式和部署資訊清單檔案。  如需詳細資訊，請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)或[專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)。  
  
### 若要變更部署資訊清單以列出多個 .NET Framework 版本  
  
1.  在發行目錄中，使用 Visual Studio 的 \[XML 編輯器\] 開啟部署資訊清單。  部署資訊清單有 .application 副檔名。  
  
2.  將 `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` 和 `</compatibleFrameworks>` 項目之間的 XML 程式碼取代為列出應用程式支援之 .NET Framework 版本的 XML。  
  
     下表顯示一些可加入至部署資訊清單的可用 .NET Framework 版本和對應 XML。  
  
    |.NET Framework 版本|XML|  
    |-----------------------|---------|  
    |4 用戶端版本|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 完整版本|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 用戶端版本|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 完整版本|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### 若要變更 app.config 檔案以列出相容的 .NET Framework 執行階段版本  
  
1.  在 \[方案總管\] 中，使用 Visual Studio 的 \[XML 編輯器\] 開啟 App.config 檔案。  
  
2.  將 `<startup>` 和 `</startup>` 項目之間的 XML 程式碼取代為 \(或在其間加入\) 列出應用程式支援之 .NET Framework 執行階段的 XML。  
  
     下表顯示一些可加入至部署資訊清單的可用 .NET Framework 版本和對應 XML。  
  
    |.NET Framework 執行階段版本|XML|  
    |---------------------------|---------|  
    |4 用戶端版本|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 完整版本|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 完整版本|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 用戶端版本|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### 若要變更應用程式資訊清單，將相依組件標示為 .NET Framework 組件  
  
1.  在發行目錄中，使用 Visual Studio 的 \[XML 編輯器\] 開啟應用程式資訊清單。  部署資訊清單有 .manifest 副檔名。  
  
2.  將 `group="framework"` 加入至 Sentinel 組件 \(`System.Core`、`WindowsBase`、`Sentinel.v3.5Client` 和 `System.Data.Entity`\) 的相依性 XML。  例如，XML 看起來應該如下：  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  將 Microsoft.Windows.CommonLanguageRuntime 的 `<assemblyIdentity>` 項目版本號碼更新為最小公因數的 .NET Framework 版本號碼。  例如，如果應用程式是以 .NET Framework 3.5 和 [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 為目標，請使用 2.0.50727.0 版本號碼，而此 XML 看起來應該如下：  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### 若要更新及重新簽署應用程式和部署資訊清單  
  
-   更新及重新簽署應用程式和部署資訊清單。  如需詳細資訊，請參閱 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> 項目](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [\<dependency\> 項目](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [組態檔結構描述](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)