---
title: "ClickOnce 安全性和部署 | Microsoft Docs"
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
  - "ClickOnce 部署"
  - "部署應用程式 [ClickOnce]"
  - "發行, ClickOnce"
  - "Windows 應用程式, ClickOnce 部署"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 安全性和部署
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 是一種部署技術，可讓您建立自行更新的 Windows 架構應用程式，這些應用程式可以在最少的使用者互動之下安裝和執行。如果您已經使用 Visual Basic 和 Visual C\# 開發自己的專案，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會針對以 ClickOnce 技術部署的應用程式，提供完整的發行和更新支援。  如需部署 Visual C\+\+ 應用程式的詳細資訊，請參閱 [Visual C\+\+ 應用程式的 ClickOnce 部署](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署克服了部署時的三大問題：  
  
-   **更新應用程式的困難：** 若使用 Microsoft Windows Installer 部署，只要應用程式更新，使用者就可以安裝更新 \(msp 檔\)，並且將它套用至已安裝的產品；而經由使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，您可以自動提供更新，  並且只會下載應用程式中經過變更的那部分，然後再從新的並存資料夾重新安裝完整、更新的應用程式。  
  
-   **對使用者電腦的影響：** 如果使用 Windows Installer 部署，應用程式通常會仰賴共用元件，而且可能會造成版本控制衝突。不過，只要使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，每個應用程式都是獨立的 \(Self\-Contained\)，而且不會干擾其他應用程式。  
  
-   **安全性權限：** Windows Installer 部署需要系統管理權限，並且只允許有限的使用者進行安裝；而 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可讓非系統管理員的使用者進行安裝，並且僅授與應用程式所必要「程式碼存取安全性」權限。  
  
 在過去，這些問題有時會讓開發人員決定建立 Web 應用程式而非 Windows 架構應用程式，雖然安裝方便，但是卻犧牲了豐富的使用者介面。  不過，在使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署的應用程式中，您可以同時擁有這兩種技術的最佳優勢。  
  
## 什麼是 ClickOnce 應用程式？  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以是任何以 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 技術發行的 Windows Presentation Foundation \(.xbap\)、Windows Form \(.exe\)、主控台應用程式 \(.exe\) 或 Office 方案 \(.dll\)。  您可以用三種不同的方式發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式：透過 Web 網頁、透過網路檔案共用，或透過 CD\-ROM 之類的媒體。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以安裝在一般使用者電腦上，如此即使電腦離線，也可以在本機上執行，或者也可以在僅限線上模式中執行，如此就不需要在一般使用者電腦上永久安裝任何項目。  如需詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自行更新。也就是說，它們可以檢查可用的更新版本，並且自動取代任何更新的檔案。  雖然開發人員可以指定更新行為，不過網路系統管理員也可以控制更新策略，例如，將更新標記為強制的。  此外，一般使用者或系統管理員都可以將更新復原為之前的版本。  如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 由於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是隔離的，因此安裝或執行  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式都不會中斷現有的應用程式。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式是獨立的，也就是說，每個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式都會安裝在針對使用者和應用程式的安全快取中，然後從中執行。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式會在 \[網際網路\] 或 \[內部網路\] 安全性區域中執行。  必要時，應用程式就可以要求更高的安全性權限。  如需詳細資訊，請參閱 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
## ClickOnce 安全性如何運作  
 核心 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安全是以憑證、程式碼存取安全性原則和 ClickOnce 信任提示為基礎。  
  
### 憑證  
 Authenticode 憑證是用來驗證應用程式發行者的真實性。  ClickOnce 使用 Authenticode 進行應用程式部署，有助於避免有害程式假扮來自現有可信任來源的合法程式。  此外，您還可選擇使用憑證來簽署應用程式和部署資訊清單，以證明檔案未遭到修改。  如需詳細資訊，請參閱 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。  憑證也可用來設定用戶端電腦上的受信任發行者清單。  如果應用程式來自信任的發行者，則不需要任何使用者互動即可安裝該應用程式。  如需詳細資訊，請參閱 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
### 程式碼存取安全性  
 程式碼存取安全性有助於限制程式碼對受保護資源的存取。  在大部分情況下，您可以選擇 \[網際網路\] 或 \[近端內部網路\] 區域來限制使用權限。  您可以使用 \[**專案設計工具**\] 中的 \[**安全性**\] 頁面，為應用程式要求適當的區域。  您也可以以有限的使用權限來偵錯應用程式，藉以模擬使用者的經驗。  如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
### ClickOnce 信任提示  
 如果應用程式要求比區域所允許的更多的使用權限，使用者會收到是否信任應用程式的提示。  使用者可決定是否信任 ClickOnce 應用程式 \(例如 Windows Form 應用程式、Windows Presentation Foundation 應用程式、主控台應用程式、XAML 瀏覽器應用程式和 Office 方案\) 執行。  如需詳細資訊，請參閱 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## ClickOnce 部署如何運作  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 核心部署架構是以兩個 XML 資訊清單檔為基礎：應用程式資訊清單和部署資訊清單。  這些檔案用來描述 ClickOnce 應用程式的安裝來源、更新方式和更新時機。  
  
### 發行 ClickOnce 應用程式  
 應用程式資訊清單會描述應用程式本身，  包括組件 \(Assembly\)、組成應用程式的相依性和檔案、必要的使用權限，以及可以取得更新的位置。  應用程式開發人員會藉由使用 Visual Studio 中的發行精靈或 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 中的資訊清單產生和編輯工具 \(Mage.exe\)，來編寫應用程式資訊清單。  如需詳細資訊，請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
 部署資訊清單會描述應用程式的部署方式，  包括應用程式資訊清單的位置以及用戶端應該要執行的應用程式版本。  
  
### 部署 ClickOnce 應用程式  
 建立部署資訊清單後，它就會複製到部署位置中。  這個位置可能是 Web 伺服器、網路檔案共用，或 CD 之類的媒體。  此外，應用程式資訊清單和所有應用程式檔案也都會複製到部署資訊清單中指定的部署位置。  這個位置可能與部署位置相同，也可能是不同的位置。  當您使用 Visual Studio 中的 \[**發行精靈**\] 時，就會自動執行複製作業。  
  
### 安裝 ClickOnce 應用程式  
 將它部署至部署位置後，一般使用者就可以按一下 Web 網頁或資料夾中表示部署資訊清單檔的圖示，藉以下載並安裝應用程式。  在大部分情況下，一般使用者都會收到一個簡單的對話方塊，詢問使用者是否確定要安裝，然後不需要另外介入就會繼續進行安裝並啟動應用程式。  如果應用程式需要更高的使用權限，或者是應用程式未由信任的憑證簽署，則此對話方塊也會要求使用者授與使用權限，以便繼續進行安裝。  雖然 ClickOnce 安裝是針對個別使用者進行，但如果有必要條件需要系統管理員權限，則可能需要更高的使用權限。  如需更高使用權限的詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
 憑證可以在電腦或企業層級受到信任，因此，以信任的憑證簽署的 ClickOnce 應用程式可以無訊息模式進行自動安裝。  如需受信任憑證的詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
 此應用程式可加入至使用者的 \[**開始**\] 功能表和 \[**控制台**\] 的 \[**新增或移除程式**\] 群組中。  不過，與其他部署技術不同的是，\[**Program Files**\] 資料夾或登錄中都不會加入任何項目，而且安裝時不需要系統管理權限。  
  
> [!NOTE]
>  您也可以防止應用程式加入至 \[**開始**\] 功能表和 \[**新增或移除程式**\] 群組中，讓它的行為實際就像是 Web 應用程式一樣。  如需詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
### 更新 ClickOnce 應用程式  
 應用程式開發人員在建立更新版本的應用程式時，會產生新的應用程式資訊清單，並將檔案複製到部署位置中 \(通常是與原始應用程式部署資料夾同層級的資料夾\)。  系統管理員會更新部署資訊清單，以便指向新版應用程式的位置。  
  
> [!NOTE]
>  Visual Studio 中的 \[**發行精靈**\] 可用來執行這些步驟。  
  
 除了部署位置以外，部署資訊清單也會包含應用程式檢查更新版本的更新位置 \(Web 網頁或網路檔案共用\)。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的 \[**發行**\] 屬性是用來指定應用程式應該檢查更新的時間和頻率。  您可以在部署資訊清單中指定更新行為，也可以利用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API，在應用程式的使用者介面中將更新行為提供成使用者選項。  此外，您可以採用 \[**發行**\] 屬性，讓更新成為強制的，或是復原為之前的版本。  如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
### 協力廠商安裝程式  
 您可以自訂 ClickOnce 安裝程式來安裝協力廠商元件和您的應用程式。  您必須有可轉散發套件 \(.exe 或 .msi 檔\)，並以非語言相關的產品資訊清單和語言特定套件資訊清單來描述該套件。  如需詳細資訊，請參閱 [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。  
  
## ClickOnce 工具  
 下表顯示您可用來產生、編輯、簽署和重新簽署應用程式和部署資訊清單的工具。  
  
|工具|描述|  
|--------|--------|  
|[專案設計工具、安全性頁](../ide/reference/security-page-project-designer.md)|簽署應用程式和部署資訊清單。|  
|[專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)|針對 Visual Basic 和 Visual C\# 應用程式來產生及編輯應用程式和部署資訊清單。|  
|[Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|針對 Visual Basic、Visual C\# 和 Visual C \+\+ 應用程式來產生應用程式和部署資訊清單。<br /><br /> 簽署及重新簽署應用程式和部署資訊清單。<br /><br /> 可以從批次指令檔和命令提示字元執行。|  
|[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|產生及編輯應用程式和部署資訊清單。<br /><br /> 簽署及重新簽署應用程式和部署資訊清單。|  
|[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)|產生應用程式資訊清單。<br /><br /> 可從 MSBuild 執行。  如需詳細資訊，請參閱 [MSBuild Reference](../msbuild/msbuild-reference.md)。|  
|[GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)|產生部署資訊清單。<br /><br /> 可從 MSBuild 執行。  如需詳細資訊，請參閱 [MSBuild Reference](../msbuild/msbuild-reference.md)。|  
|[SignFile Task](../msbuild/signfile-task.md)|簽署應用程式和部署資訊清單。<br /><br /> 可從 MSBuild 執行。  如需詳細資訊，請參閱 [MSBuild Reference](../msbuild/msbuild-reference.md)。|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|開發您自己的應用程式來產生應用程式和部署資訊清單。|  
  
 下表顯示要在下列瀏覽器中支援 ClickOnce 應用程式所需的 .NET Framework 版本。  
  
|瀏覽器|.NET Framework 版本|  
|---------|-----------------------|  
|Internet Explorer|2.0、3.0、3.5、3.5 SP1、4|  
|Firefox|2.0 SP1、3.5 SP1、4|  
  
## 請參閱  
 [Windows Vista 的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 COM 元件](../deployment/deploying-com-components-with-clickonce.md)   
 [從命令列建置 ClickOnce 應用程式](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)