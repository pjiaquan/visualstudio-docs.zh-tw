---
title: "&lt;deployment&gt; 項目 (ClickOnce 部署) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> 項目 [ClickOnce 部署資訊清單]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# &lt;deployment&gt; 項目 (ClickOnce 部署)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別用於更新部署及公開至系統的屬性。  
  
## 語法  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## 項目和屬性  
 `deployment` 項目是必要項，而且位於 `urn:schemas-microsoft-com:asm.v1` 命名空間中。  項目具有下列屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`install`|必要項。  指定此應用程式是否會定義出現在 Windows \[**開始**\] 功能表和 \[控制台\] 內的 \[**新增或移除程式**\] 應用程式中。  有效值為 `true` 和 `false`。  如果為 `false`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 就一定會從網路執行此應用程式的最新版本，並且將不會辨認 `subscription` 項目。|  
|`minimumRequiredVersion`|選擇項。  指定此應用程式能在用戶端上執行的最小版本。  如果應用程式的版本號碼小於部署資訊清單中提供的版本號碼，應用程式就不會執行。  版本號碼必須以 `N.N.N.N` 格式指定，其中的 `N` 是不帶正負號的整數 \(Unsigned Integer\)。  如果 `install` 屬性為 `false`，就不能設定 `minimumRequiredVersion`。|  
|`mapFileExtensions`|選擇項。  預設值為 `false`。  如果為 `true`，部署中的所有檔案必須具有 .deploy 副檔名。  一旦從 Web 伺服器下載這些檔案，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 就會立刻從它們移除這個副檔名。  如果您是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 發行應用程式，它會自動替所有檔案加上這個副檔名。  這個參數讓 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署內的所有檔案，都可以從封鎖具有「不安全」副檔名 \(例如 .exe\) 之檔案傳輸的 Web 伺服器下載。|  
|`disallowUrlActivation`|選擇項。  預設值為 `false`。  如果是 `true`，就無法經由按一下 URL 或者在 Internet Explorer 中輸入 URL 來啟動安裝的應用程式。  如果不存在 `install` 屬性，就會忽略這個屬性。|  
|`trustURLParameters`|選擇項。  預設值為 `false`。  如果是 `true`，URL 就可以包含要傳遞至應用程式的查詢字串參數，很像將命令列引數傳遞給命令列應用程式。  如需詳細資訊，請參閱 [如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)。<br /><br /> 如果 `disallowUrlActivation` 屬性為 `true`，就應該將 `trustUrlParameters` 從資訊清單中排除，或將它明確設定為 `false`。|  
  
 `deployment` 項目也含有下列子項目。  
  
## Subscription \- 訂閱  
 選擇項。  包含 `update` 項目。  `subscription` 項目沒有任何屬性。  如果沒有 `subscription` 項目，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式就絕對不會掃描更新。  如果 `deployment` 項目的 `install` 屬性為 `false`，由於從網路啟動的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式一定會使用最新版本，因此會忽略 `subscription` 項目。  
  
## update  
 必要項。  這個項目是 `subscription` 項目的子系，並包含 `beforeApplicationStartup` 或  `expiration` 項目。  `beforeApplicationStartup` 和 `expiration` 無法同時在相同的部署資訊清單中被指定。  
  
 `update` 項目沒有任何屬性。  
  
## beforeApplicationStartup  
 選擇項。  這個項目是 `update` 項目的子項目，而且沒有屬性。  當 `beforeApplicationStartup` 項目存在時，如果用戶端位於線上，便會在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檢查更新時封鎖應用程式。  如果不存在這個項目，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會先根據為 `expiration` 項目指定的值來掃描更新。  `beforeApplicationStartup` 和 `expiration` 無法同時在相同的部署資訊清單中被指定。  
  
## expiration  
 選擇項。  這個項目是 `update` 項目的子系，而且本身沒有子系。  `beforeApplicationStartup` 和 `expiration` 無法同時在相同的部署資訊清單中被指定。  更新檢查時若偵測到更新版本，新版本會在現有版本執行時快取。  下次啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時會接著安裝新版本。  
  
 `expiration` 項目可支援下列屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`maximumAge`|必要項。  識別應用程式每次執行更新檢查的間隔時間。  時間的單位由 `unit` 屬性決定。|  
|`unit`|必要項。  識別 `maximumAge` 的時間單位。  有效單位為 `hours`、`days` 及 `weeks`。|  
  
## deploymentProvider  
 對於 .NET Framework 2.0，如果部署資訊清單包含 `subscription` 區段，這個項目就是必要的。  對於 .NET Framework 3.5 \(含\) 以後版本，此項目是選擇性的，而且會預設為發現部署資訊清單的伺服器和檔案路徑。  
  
 這個項目是 `deployment` 項目的子項，並具備下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`codebase`|必要項。  識別用來更新 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的部署資訊清單位置 \(統一資源識別元 \(URI\)\)。  此項目也允許轉送 CD 式安裝的更新位置。  必須是有效的 URI。|  
  
## 備註  
 您可以設定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，以便在啟動時掃描更新、在啟動後掃描更新，或是絕不檢查更新。  若要在啟動時掃描更新，請確定 `beforeApplicationStartup` 項目在 `update` 項目之下。  若要在啟動後掃描更新，請確定 `expiration` 項目存在於 `update` 項目之下，並有提供更新間隔。  
  
 若要停用檢查更新，請移除 `subscription` 項目。  即使在部署資訊清單中指定絕不掃描更新，您還是可以使用 <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> 方法以手動方式檢查更新。  
  
 如需 deploymentProvider 與更新之關係的詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
## 範例  
 在下列程式碼範例中，會說明 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中的 `deployment` 項目。  此範例會使用 `deploymentProvider` 項目來指出慣用的更新位置。  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## 請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)