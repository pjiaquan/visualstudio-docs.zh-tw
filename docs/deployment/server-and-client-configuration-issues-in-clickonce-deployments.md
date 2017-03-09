---
title: "ClickOnce 部署中的伺服器和用戶端組態問題 | Microsoft Docs"
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
  - "ClickOnce 部署, 疑難排解"
  - "部署應用程式, ClickOnce"
  - "疑難排解 ClickOnce 部署"
  - "Windows 應用程式, ClickOnce 部署"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 部署中的伺服器和用戶端組態問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果在 Windows Server 使用網際網路資訊服務 \(IIS\)，而且部署含有 Windows 無法辨認的檔案類型，例如 Microsoft Word 檔案，這樣 IIS 將會拒絕傳輸該檔案，您的部署就無法成功。  
  
 此外，一些 Web 伺服器和 Web 應用程式軟體，例如 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，含有您無法下載的檔案和檔案類型的清單。  例如，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 會防止下載所有的 Web.config 檔案，  因為這些檔案可能會包含使用者名稱和密碼等機密資訊。  
  
 雖然這個限制不會對下載核心的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檔案 \(如資訊清單和組件\) 造成問題，卻有可能防止您下載一部分屬於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的資料檔案。  在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 中，您可以藉由從 IIS 組態管理員中移除禁止下載此類檔案的處理常式，以解決這個錯誤。  如需詳細資訊，請參閱 IIS 伺服器文件。  
  
 某些 Web 伺服器可能會封鎖具有類似 .dll、.config 和 .mdf 等副檔名的檔案。  Windows 架構應用程式通常會包含這些副檔名的檔案。  如果使用者嘗試執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，但應用程式存取 Web 伺服器上封鎖的檔案，則會發生錯誤。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 預設會用 ".deploy" 副檔名發行每個應用程式檔案，而不是解除封鎖所有的副檔名。  因此，系統管理員只需要將 Web 伺服器設定為解除封鎖下列三種副檔名：  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 不過，您可以在[Publish Options Dialog Box](http://msdn.microsoft.com/zh-tw/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)上清除 \[**使用 ".deploy" 副檔名**\] 選項，以停用這個選項；在這個狀況下，您必須將 Web 伺服器設定為解除封鎖這個應用程式中使用的所有副檔名。  
  
 例如，如果您使用未安裝 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的 IIS，或其他 Web 伺服器 \(例如 Apache\)，則必須設定 .manifest、.application 和 .deploy。  
  
## ClickOnce 和 Secure Sockets Layer \(SSL\)  
 除非 Internet Explorer 發出關於 SSL 憑證的提示，否則 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可透過 SSL 順利運作。  當憑證有問題時可能會引發提示，例如當站台名稱不符或者憑證已逾期。  若要讓 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 能透過 SSL 連接運作，請確定此憑證是最新的，而且憑證資料符合站台資料。  
  
## ClickOnce 和 Proxy 驗證  
 從 .NET Framework 3.5 開始，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 提供 Windows 整合式 Proxy 驗證支援。  這不需要特定的 machine.config 指示詞。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不支援其他驗證通訊協定，如「基本」或「摘要式」驗證。  
  
 您也可以將 Hotfix 套用至 .NET Framework 2.0，以啟用此功能。  如需詳細資訊，請參閱 http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730。  
  
 如需詳細資訊，請參閱 [\<defaultProxy\> 項目 \(網路設定\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md)。  
  
## ClickOnce 和 Web 瀏覽器相容性  
 就目前而言，只有在使用 Internet Explorer 開啟部署資訊清單的 URL 時，才會啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 安裝。  只有當 Internet Explorer 設定為預設的 Web 瀏覽器時，才會成功啟動從另一個應用程式 \(例如 Microsoft Office Outlook\) 啟動 URL 的部署。  
  
> [!NOTE]
>  如果部署提供者不是空白，或是安裝了 Microsoft .NET Framework 助理擴充程式，則支援 Mozilla Firefox。  此擴充程式隨 .NET Framework 3.5 SP1 一起封裝。  NPWPF 外掛程式會在需要時啟動，以支援 XBAP。  
  
## 透過瀏覽器指令碼啟動 ClickOnce 應用程式  
 如果您開發了使用 Active Scripting 啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的自訂 Web 網頁，您可能會發現該應用程式無法在某些電腦上啟動。  Internet Explorer 包含一個 \[**自動提示檔案下載**\] 設定，這個設定會影響這個行為。  影響這個行為的這個設定位於 \[**選項**\] 功能表的 \[**安全性**\] 索引標籤上。  這個設定名為 \[**自動提示下載檔案**\]，列在 \[**下載**\] 分類底下。  內部網路網頁的這項屬性預設為 \[**啟用**\]，而 Internet 網頁的這項屬性則預設為 \[**停用**\]。  當這項設定為 \[**停用**\] 時，任何嘗試以程式設計方式啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的動作 \(例如，將其 URL 指派給 `document.location` 屬性\) 都會被封鎖。  這種情形下，使用者只能透過使用者啟始的下載來啟動應用程式，例如，按一下設定為應用程式之 URL 的超連結 \(Hyperlink\)。  
  
## 其他伺服器組態問題  
  
##### 必須有管理員使用權限  
 如果要使用 HTTP 發行，必須有目標伺服器的管理員使用權限。  IIS 要求這項權限等級。  如果發行不使用 HTTP，只需要目標路徑的寫入權限。  
  
##### 伺服器驗證問題  
 在發行到已關閉「匿名存取」的遠端伺服器時，您會收到下列警告：  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  如果站台所要求的憑證與預設憑證不同，且在安全性對話方塊中，出現提示您是否要儲存所提供憑證以供未來工作階段使用時，按一下 \[**確定**\] 就可以使 NTLM \(NT 挑戰\-回應\) 驗證方式順利執行。  不過，這個解決方法無法應用於基本驗證。  
  
## 使用協力廠商 Web 伺服器  
 如果從不是 IIS 的 Web 伺服器部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，當伺服器傳回關鍵 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檔案 \(例如部署資訊清單和應用程式資訊清單\) 不正確的內容類型時，您可能會遇到問題。  若要解決這個問題，請參閱 Web 伺服器的說明文件中有關如何將新的內容類型加入至伺服器的資訊，並確認加入了下表列出的所有副檔名對應的內容類型。  
  
|副檔名|內容類型|  
|---------|----------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce 和對應磁碟機  
 如果使用 Visual Studio 來發行 ClickOnce 應用程式，不能指定對應磁碟機做為安裝位置。  不過，您可以使用資訊清單產生器和編輯器 \(Mage.exe 和 MageUI.exe\)，將 ClickOnce 應用程式修改為從對應磁碟機安裝。  如需詳細資訊，請參閱 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) 和 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)。  
  
## 不支援使用 FTP 通訊協定安裝應用程式  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 支援從任何 HTTP 1.1 Web 伺服器或檔案伺服器安裝應用程式。  但不支援使用 FTP \(檔案傳輸通訊協定\) 安裝應用程式。  您只能使用 FTP 發行應用程式。  下表摘要說明了差別之處：  
  
|URL 類型|描述|  
|------------|--------|  
|ftp:\/\/|您可以使用此通訊協定發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。|  
|http:\/\/|您可以使用此通訊協定安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。|  
|https:\/\/|您可以使用此通訊協定安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。|  
|file:\/\/|您可以使用此通訊協定安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。|  
  
## Windows XP SP2：Windows 防火牆  
 Windows XP SP2 預設啟用 Windows 防火牆。  如果您在安裝有 Windows XP 的電腦上開發應用程式，仍然可以從執行 IIS 的本機伺服器發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。  不過，除非開啟 Windows 防火牆，否則您無法從其他電腦存取執行 IIS 的伺服器。  如需管理 Windows 防火牆的相關指示，請參閱 Windows 說明。  
  
## Windows Server：啟用 FrontPage Server Extensions  
 使用 HTTP 將應用程式發行至 Windows Web 伺服器時，需要 Microsoft 的 FrontPage Server Extensions。  
  
 Windows Server 預設不會安裝 FrontPage Server Extensions。  如果要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 發行到 Windows Server 網頁伺服器 \(透過 FrontPage Server Extensions 使用 HTTP\)，必須先安裝 FrontPage Server Extensions。  您可以使用 Windows Server 中的 \[管理您的伺服器\] 系統管理工具完成此安裝。  
  
## Windows Server：鎖定的內容類型  
 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] 上的 IIS 會鎖定某些已知內容類型 \(例如 .htm、.html、.txt 等\) 以外的所有檔案類型。  若要使用這部伺服器啟用部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，您必須變更 IIS 設定，允許下載下列檔案類型：.application、.manifest，以及應用程式使用的其他自訂檔案類型。  
  
 如果您使用 IIS 伺服器進行部署，請執行 inetmgr.exe 並為預設的 Web 網頁加入新的檔案類型：  
  
-   針對 .application 和 .manifest 副檔名，MIME 類型應該是 "application\/x\-ms\-application"。 對於其他檔案類型，MIME 類型應該是 "application\/octet\-stream"。  
  
-   如果您以副檔名 "\*" 和 MIME 類型 "application\/octet\-stream"，建立 MIME 類型，它會允許下載未封鎖的檔案類型   \(不過，無法下載封鎖的檔案類型，例如 .aspx 和 .asmx\)。  
  
 如需在 Windows Server 上設定 MIME 類型的特定指示，請參閱 Microsoft 知識庫文件 KB326965＜IIS 6.0 不支援未知的 MIME 類型＞，網址為 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;zh\-tw;326965](http://support.microsoft.com/default.aspx?scid=kb;zh-tw;326965) \(英文\)。  
  
## 內容類型對應  
 透過 HTTP 發行時，.application 檔案的內容類型 \(也稱為 MIME 類型\) 應該是 "application\/x\-ms\-application"。 如果在伺服器上已安裝 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，這將會自動設定。  如果沒有安裝，則您必須為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式 vroot \(或整個伺服器\) 建立 MIME 類型關聯。  
  
 如果您使用 IIS 伺服器進行部署，請執行 inetmgr.exe，並為 .application 副檔名加入新的內容類型 "application\/x\-ms\-application"。  
  
## HTTP 壓縮問題  
 經由使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，您可以執行使用 HTTP 壓縮的下載作業，HTTP 壓縮是在將資料流傳送至用戶端以前，使用 GZIP 演算法來壓縮資料流的 Web 伺服器技術。  用戶端，在此情況下也就是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，會在讀取檔案之前先解壓縮資料流。  
  
 如果使用 IIS，您就能輕易地啟用 HTTP 壓縮。  不過，當您啟用 HTTP 壓縮時，它只會針對特定檔案類型而啟用，亦即 HTML 和文字檔。  若要啟用組件 \(.dll\)、XML \(.xml\)、部署資訊清單 \(.deploy\) 及應用程式資訊清單 \(.manifest\) 的壓縮，您必須將這些檔案類型加入至 IIS 的壓縮類型清單中。  將這些檔案類型加入至部署之前，只有文字檔和 HTML 檔案會進行壓縮。  
  
 如需 IIS 的詳細指示，請參閱[如何指定 HTTP 壓縮的其他文件類型](http://go.microsoft.com/fwlink/?LinkId=178459)。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)