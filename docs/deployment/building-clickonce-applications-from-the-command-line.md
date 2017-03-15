---
title: "從命令列建置 ClickOnce 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce 部署, 從命令列"
  - "發行"
  - "發行, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# 從命令列建置 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，您可以從命令列建置專案，即使專案是在整合式開發環境 \(IDE\) 中建立的。  事實上，您可以在只安裝 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的另一部電腦上，重新建置以 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 所建立的專案。  這可讓您使用自動化處理序 \(例如在集中建置實驗室，或使用超越建置專案本身範圍的進階指令碼技術\)，重新產生組建。  
  
## 使用 MSBuild 重新產生 ClickOnce 應用程式部署  
 當您在命令列叫用 msbuild \/target:publish，它會告訴 MSBuild 系統，建置專案並在發行資料夾中建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  這相當於在 IDE 中選取 \[**發行**\] 命令。  
  
 這個命令會執行 msbuild.exe，它位於 Visual Studio 命令提示字元環境中的路徑。  
  
 "target" 向 MSBuild 指示如何處理命令。  主要目標為「建置」目標和「發行」目標。  建置目標相當於在 IDE 中選取 \[建置\] \(或按 F5\) 命令。  如果您只要建置專案，可以輸入 `msbuild`，完成此作業。  因為建置目標是所有由 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 所產生專案的預設目標，所以這個命令有作用。  這表示您不必明確指定建置目標。  因此，輸入 `msbuild` 與輸入 `msbuild /target:build` 會執行相同作業。  
  
 `/target:publish` 命令告訴 MSBuild，叫用發行目標。  發行目標相依於建置目標。  這表示發行作業是建置作業的超集。  例如，如果您變更其中一個 Visual Basic 或 C\# 原始程式檔，則發行作業會自動重新建置對應的組件。  
  
 如需使用 Mage.exe 命令列工具建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資料清單，產生完整 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## 使用 MSBuild 建立和建置基本的 ClickOnce 應用程式  
  
#### 若要建立和發行 ClickOnce 專案  
  
1.  從 \[**檔案**\] 功能表中，按一下 \[**新增專案**\]。  \[**新增專案**\] 對話方塊隨即出現。  
  
2.  選取 \[**Windows 應用程式**\]，並為它命名為 `CmdLineDemo`。  
  
3.  從 \[**建置**\] 功能表中，按一下 \[**發行**\] 命令。  
  
     這個步驟可確保專案正確設定為產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署。  
  
     \[發行精靈\] 隨即出現。  
  
4.  在 \[發行精靈\] 中，按一下 \[**完成**\]。  
  
     Visual Studio 隨即會產生和顯示名稱為 Publish.htm 的預設 Web 網頁。  
  
5.  儲存專案，並記下儲存專案的資料夾位置。  
  
 上面的步驟會建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 專案，這個專案已經第一次發行。  現在您可以在 IDE 以外重新產生組建。  
  
#### 若要從命令列重新產生組建  
  
1.  結束 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
2.  從 Windows \[**開始**\] 功能表，依序按一下 \[**所有程式**\]、\[**Microsoft Visual Studio**\]、\[**Visual Studio Tools**\] 和 \[**Visual Studio 命令提示字元**\]。  這應該會開啟一個命令提示字元，其位置便在目前使用者的根資料夾中。  
  
3.  在 \[**Visual Studio 命令提示字元**\]，將目前目錄切換到前面剛建置好的專案位置。  例如，輸入 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`。  
  
4.  若要移除上面＜若要建立和建置 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 專案＞中產生的現有檔案，請輸入 `rmdir /s publish`。  
  
     這個步驟是選擇性，但這個動作會確保所有新檔案都是由此命令列組建產生的。  
  
5.  輸入 `msbuild /target:publish`。  
  
 上面的步驟將會在專案中名稱為 \[**Publish**\] 的子資料夾，產生完整的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署。  CmdLineDemo.application 是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署資訊清單。  資料夾 CmdLineDemo\_1.0.0.0 包含檔案 CmdLineDemo.exe 和 CmdLineDemo.exe.manifest \([!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單\)。  Setup.exe 是啟動載入器 \(Bootstrapper\)，預設為安裝 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  DotNetFX 資料夾包含 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的可轉散發套件。  這些就是透過 Web、UNC 或 CD\/DVD 部署應用程式所需的完整檔案集。  
  
## 發行屬性  
 當您用以上的程序發行應用程式時，\[發行精靈\] 會將下列屬性插入專案檔。  這些屬性直接影響 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的產生方式。  
  
 CmdLineDemo.vbproj \/ CmdLineDemo.csproj：  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 您可以在命令列覆寫這些屬性，而不需變更專案檔本身。  例如，下列將會建置不含啟動載入器的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式部署：  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，從 \[**專案設計工具**\] 的 \[**發行**\]、\[**安全性**\] 和 \[**簽章**\] 屬性頁面，控制發行屬性。  以下是發行屬性的描述，以及在應用程式設計工具的各個屬性頁中如何設定屬性的指示：  
  
-   `AssemblyOriginatorKeyFile` 決定簽署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單所使用的金鑰檔。  這個金鑰也可以用來簽署組件的強式名稱。  在 \[**專案設計工具**\] 的 \[**簽章**\] 頁面中，設定這個屬性。  
  
 下列屬性在 \[**安全性**\] 頁中設定：  
  
-   \[**啟用 ClickOnce 安全性設定**\] 可決定是否產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單。  最初建立專案時，產生 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單的功能預設為關閉。  當您第一次發行時，精靈會自動開啟這個旗標。  
  
-   **TargetZone** 決定發出給 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單的信任層級。  可能值為 "Internet"、"LocalIntranet" 和 "Custom"。  Internet 和 LocalIntranet 將會造成預設權限集發出至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單。  LocalIntranet 為預設值，基本上表示完全信任。  Custom 指定只有基底 app.manifest 檔案中明確指定的權限，才會發出至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單。  app.manifest 檔案是部分資訊清單檔案，只包含信任資訊定義。  它是隱藏檔案，當您在 \[**安全性**\] 頁面中設定權限時，便會自動加入至專案。  
  
 下列屬性在 \[**發行**\] 頁面中設定：  
  
-   `PublishUrl` 是應用程式在 IDE 中發行時的目標位置。  如果未指定 `InstallUrl` 或 `UpdateUrl` 屬性，就會將它插入 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單。  
  
-   `ApplicationVersion` 指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的版本。  這是四碼版本號碼。  如果最後一碼是 "\*"，則在建置時間 `ApplicationRevision` 會取代資訊清單中所插入的值。  
  
-   `ApplicationRevision` 會指定修訂。  這是整數，每次您在 IDE 發行時，這個整數會累加。  請注意，對於在命令列執行的組建，它不會自動累加。  
  
-   `Install` 可以判斷應用程式是安裝的應用程式還是從 Web 執行的應用程式。  
  
-   `InstallUrl` \(未顯示\) 是使用者安裝應用程式的來源位置。  如果指定，這個值就會燒錄至 setup.exe 啟動載入器 \(如果已啟用 `IsWebBootstrapper` 屬性\)。  如果未指定 `UpdateUrl`，也會將此值插入應用程式資訊清單。  
  
-   `SupportUrl` \(未顯示\) 是 \[**新增或移除程式**\] 對話方塊中已安裝程式的連結位置。  
  
 下列屬性在 \[**應用程式更新**\] 對話方塊 \(從 \[**發行**\] 頁存取\) 中設定。  
  
-   `UpdateEnabled` 指出應用程式是否應該檢查更新檔。  
  
-   `UpdateMode` 指定前景更新或背景更新。  
  
-   `UpdateInterval` 指定應用程式應該檢查更新檔的頻率。  
  
-   `UpdateIntervalUnits` 指定 `UpdateInterval` 值的單位：小時、天數或週數。  
  
-   `UpdateUrl` \(未顯示\) 是應用程式將接收更新檔的來源位置。  如果指定，這個值會插入應用程式資訊清單。  
  
-   下列屬性在 \[**發行選項**\] 對話方塊 \(從 \[**發行**\] 頁面存取\) 中設定。  
  
-   `PublisherName` 指定發行者的名稱，當安裝或執行應用程式時，它會顯示在提示中。  在安裝的應用程式案例中，它也用來指定 \[**開始**\] 功能表上的資料夾名稱。  
  
-   `ProductName` 指定產品的名稱，當安裝或執行應用程式時，它會顯示在提示中。  在安裝的應用程式案例中，它也用來指定 \[**開始**\] 功能表上的捷徑名稱。  
  
-   下列屬性在 \[**必要條件**\] 對話方塊 \(從 \[**發行**\] 頁面存取\) 中設定。  
  
-   `BootstrapperEnabled` 能夠判斷是否要產生 setup.exe 啟動載入器。  
  
-   `IsWebBootstrapper` 能夠判斷 setup.exe 啟動載入器是透過 Web 還是以磁碟架構的模式運作。  
  
## InstallURL、SupportUrl、PublishURL 和 UpdateURL  
 下表顯示 ClickOnce 部署的四個 URL 選項。  
  
|URL 選項|描述|  
|------------|--------|  
|`PublishURL`|如果您要將 ClickOnce 應用程式發行至網站時需要。|  
|`InstallURL`|選擇項。  如果安裝網站不同於 `PublishURL` 時，請設定這個 URL 選項。  例如，您可以將 `PublishURL` 設為 FTP 路徑，並且將 `InstallURL` 設為 Web URL。|  
|`SupportURL`|選擇項。  如果支援網站不同於 `PublishURL` 時，請設定這個 URL 選項。  例如，您可以將 `SupportURL` 設定為您公司的客戶支援網站。|  
|`UpdateURL`|選擇項。  如果更新位置不同於 `InstallURL` 時，請設定這個 URL 選項。  例如，您可以將 `PublishURL` 設為 FTP 路徑，並且將 `UpdateURL` 設為 Web URL。|  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)