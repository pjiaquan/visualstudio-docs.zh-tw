---
title: "ClickOnce 部署中的安全性、版本控制和資訊清單問題 | Microsoft Docs"
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
  - "ClickOnce 應用程式, 資訊清單問題"
  - "ClickOnce 應用程式, 安全性問題"
  - "ClickOnce 應用程式, 版本控制問題"
  - "ClickOnce 應用程式, Windows Vista 使用者帳戶控制"
  - "資料清單 [ClickOnce]"
  - "安全性, ClickOnce 應用程式"
  - "使用者帳戶控制, ClickOnce 應用程式"
  - "版本控制, ClickOnce 應用程式"
  - "Windows 7, ClickOnce 部署"
  - "Windows Vista, ClickOnce 部署"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 部署中的安全性、版本控制和資訊清單問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安全性、應用程式版本和資訊清單語法及語意 \(Semantics\) 有多種問題，可能導致 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署無法成功。  
  
## ClickOnce 與 Windows Vista 使用者帳戶控制  
 在 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 中，應用程式預設會以標準使用者的身分執行，即使目前的使用者使用有系統管理員使用權限的帳戶登入。  如果應用程式必須執行需要系統管理員使用權限的動作，它會告知作業系統，由作業系統提示使用者輸入其系統管理員認證。  這項功能稱為「使用者帳戶控制」\(UAC\)，可防止應用程式在沒有使用者明確核准的情況下，做出可能影響整個作業系統的變更。  Windows 應用程式會在其應用程式資訊清單的 `trustInfo` 區段指定 `requestedExecutionLevel` 屬性，宣告需要此使用權限提高。  
  
 由於應用程式有暴露在安全性升級攻擊下的風險，因此如果用戶端啟用 UAC，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式便無法要求使用權限提高。  任何嘗試將 `requestedExecutionLevel` 屬性設為 `requireAdministrator` 或 `highestAvailable` 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，都不會安裝在 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 上。  
  
 在某些情況下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可能會因為 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 上的安裝程式偵測邏輯，而嘗試以系統管理員使用權限執行。  在這種情況下，您可以將應用程式資訊清單中的 `requestedExecutionLevel` 屬性設為 `asInvoker`。  這可讓應用程式本身在不必升級的情況下執行。[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 會自動將此屬性加入到所有應用程式資訊清單。  
  
 如果您部署的應用程式在其整個存留期 \(Lifetime\) 都需要系統管理員使用權限，請考慮改用 Windows Installer \(MSI\) 技術部署應用程式。  如需詳細資訊，請參閱 [Windows 安裝程式的基本概念](../extensibility/internals/windows-installer-basics.md)。  
  
## 線上應用程式配額以及部分信任的應用程式  
 如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是在線上執行，而不是經由安裝而執行，那麼它就必須符合針對線上應用程式所撥出的配額。  此外，在部分信任狀態下執行的網路應用程式 \(例如使用一組有限的安全性權限\) 不能大於配額大小的一半。  
  
 如需如何變更線上應用程式配額的詳細資訊以及指示，請參閱 [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。  
  
## 版本控制問題  
 如果對組件指派強式名稱 \(Strong Name\)，並且遞增組件版本號碼以反映應用程式更新，您就可能會遭遇問題。  以強式名稱組件的參考進行編譯的任何組件，都必須重新自我編譯，否則組件就會嘗試參考較舊的版本。  組件這麼做的原因，是因為組件在其繫結要求中使用的是舊版本值。  
  
 例如，假設您擁有 1.0.0.0 版且位於其自身專案中的強式名稱組件，  在編譯組件後，您將它加入為包含主要應用程式之專案的參考。  如果更新組件，將版本遞增為 1.0.0.1，並試圖將之部署而不重新編譯應用程式，應用程式將無法在執行階段載入組件。  
  
 這項錯誤只會在以手動編輯 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單時發生；如果使用 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] 產生您的部署，就應該不會發生這項錯誤。  
  
## 在資訊清單內指定個別的 .NET Framework 組件  
 如果您已手動編輯 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，使其參考舊版的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 組件，則您的應用程式將無法載入。  例如，如果您加入 System.Net 組件的參考，而該組件所用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本早於資訊清單內指定的版本，則會發生錯誤。  一般情形下，您不應該嘗試指定個別 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 組件的參考，因為您的應用程式執行時所用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本會指定為應用程式資訊清單內的相依性。  
  
## 資訊清單剖析問題  
 由 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用的資訊清單檔案都是 XML 檔，而且必須是語式正確 \(Well\-Formed\) 和有效的：這些檔案必須遵從 XML 語法規則，並且只使用相關 XML 結構描述中定義的項目和屬性。  
  
 資訊清單檔內某個可能會發生問題的項目選取了包含特殊字元 \(例如單引號或雙引號\) 的應用程式名稱，  應用程式的名稱是其 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 識別的一部分。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 目前不會剖析包含特殊字元的識別。  如果您的應用程式無法啟動，請確定該名稱內只使用字母和數字字元，然後再嘗試部署一次。  
  
 如果您以手動方式編輯部署資訊清單或應用程式資訊清單，可能會不小心損壞了資訊清單，  損壞的資訊清單會造成無法正確進行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安裝。  在執行階段按一下 \[**ClickOnce 錯誤**\] 對話方塊上的 \[**詳細資料**\]，並參閱記錄檔中的錯誤訊息，即可偵錯這種錯誤。  記錄檔會列出下列其中一個訊息：  
  
-   語法錯誤的描述，以及發生錯誤的行數和字元位置。  
  
-   在資訊清單結構描述的違規中使用的項目或屬性的名稱。  如果是手動將 XML 加入資訊清單，就必須比較您的加入項目和資訊清單結構描述。  如需詳細資訊，請參閱 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)和 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
-   ID 衝突。  在部署和應用程式資訊清單中的相依性參考，必須在 `name` 和 `publicKeyToken` 屬性都是唯一的。  如果兩個屬性符合資訊清單內的任何兩個項目，資訊清單剖析就不會成功。  
  
## 手動變更資訊清單或應用程式的預防措施  
 您在更新應用程式資訊清單時，必須重新簽署應用程式資訊清單和部署資訊清單。  部署資訊清單包含應用程式資訊清單的參考，而這個應用程式資訊清單中則包含該檔案的雜湊及其數位簽章。  
  
### 部署提供者使用上的預防措施  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單中有 `deploymentProvider` 屬性，這個屬性指向應用程式安裝和服務位置的完整路徑：  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 這個路徑是在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 建立應用程式時設定，已安裝的應用程式一定要有此路徑。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安裝程式會從這個路徑所指向的標準位置安裝應用程式並尋找更新。  如果您使用 **xcopy** 命令，將 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式複製到不同位置，但未變更 `deploymentProvider` 屬性，當 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 嘗試下載應用程式時，它仍然會參考到此原始位置。  
  
 如果您要移動或複製應用程式，同時必須更新 `deploymentProvider` 路徑，讓用戶端從新位置實際安裝。  如果您有已安裝的應用程式，更新這個路徑通常都是件重要的事。  對於永遠透過原始 URL 啟動的線上應用程式，設定 `deploymentProvider` 為選擇項。  如果已設定 `deploymentProvider`，就會接受它，否則用來啟動應用程式的 URL 將做為基礎 URL，用來下載應用程式檔案。  
  
> [!NOTE]
>  每次更新資訊清單時，都必須再次加以簽署。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)