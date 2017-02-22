---
title: "&lt;entryPoint&gt; 項目 (ClickOnce 應用程式) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> 項目 [ClickOnce 應用程式資訊清單]"
  - "資料清單 [ClickOnce], entryPoint 項目"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;entryPoint&gt; 項目 (ClickOnce 應用程式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別當這個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式在用戶端電腦上執行時，所應該執行的組件。  
  
## 語法  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## 項目和屬性  
 `entryPoint` 項目是必要項，而且位於 `urn:schemas-microsoft-com:asm.v2` 命名空間中。  應用程式資訊清單內只能定義一個 `entryPoint` 項目。  
  
 `entryPoint` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`name`|選擇項。  .NET Framework 不使用這個值。|  
  
 `entryPoint` 具有下列項目。  
  
## assemblyIdentity  
 必要項。  `assemblyIdentity` 的角色及其屬性都定義於 [\<assemblyIdentity\> 項目](../deployment/assemblyidentity-element-clickonce-application.md) 中。  
  
 此項目的 `processorArchitecture` 屬性和定義在應用程式資訊清單內其他地方之 `assemblyIdentity` 內的 `processorArchitecture` 屬性必須相符。  
  
## commandLine  
 必要項。  必須是 `entryPoint` 項目的子系。  它沒有子項目並具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`file`|必要項。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式之啟動組件的本機參考。  這個值不能包含正斜線 \(\/\) 或反斜線 \(\\\) 路徑分隔符號。|  
|`parameters`|必要項。  描述對進入點採取的動作。  唯一有效的值是 `run`，如果提供空字串，便會假設為 `run`。|  
  
## customHostRequired  
 選擇項。  若包含此項，會指定這個部署含有將在自訂主應用程式內部署的元件，而且不是獨立的應用程式。  
  
 如果有這個項目的話，就不能有 `assemblyIdentity` 和 `commandLine` 項目。  若有，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會在安裝期間引發驗證錯誤。  
  
 這個項目沒有任何屬性和子系。  
  
## customUX  
 選擇項。  指定應用程式由自訂安裝程式來安裝與維護，而且不會建立 \[開始\] 功能表項目、捷徑或 \[新增或移除程式\] 項目。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 包含 customUX 項目的應用程式，必須提供使用 <xref:System.Deployment.Application.InPlaceHostingManager> 類別的自訂安裝程式來執行安裝作業。  具有此項目的應用程式，在安裝時並不能用按兩下其資訊清單或 setup.exe 必要條件啟動載入器來進行。  自訂安裝程式可以建立 \[開始\] 功能表項目、捷徑和 \[新增或移除程式\] 項目。  如果自訂安裝程式不會建立 \[新增或移除程式\] 項目，就必須儲存 <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> 屬性所提供的訂閱識別碼，並讓使用者在以後藉由呼叫 <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> 方法來解除安裝應用程式。  如需詳細資訊，請參閱 [逐步解說：為 ClickOnce 應用程式建立自訂安裝程式](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)。  
  
## 備註  
 此項目會識別 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的組件和進入點。  
  
 您不能使用 `commandLine` 來對應用程式在執行階段傳遞參數。  您可以從應用程式的 <xref:System.AppDomain> 存取 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的查詢字串參數。  如需詳細資訊，請參閱 [如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)。  
  
## 範例  
 下列程式碼範例說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式之應用程式資訊清單中的 `entryPoint` 項目。  這個程式碼範例是 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)主題完整範例的一部分。  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)