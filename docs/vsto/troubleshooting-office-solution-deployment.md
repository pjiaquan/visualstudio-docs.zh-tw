---
title: "Office 方案部署疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發]，疑難排解"
  - "Visual Studio 中的 Office 程式開發，疑難排解"
  - "開發應用程式 [Visual Studio 中的 Office 程式開發]，疑難排解"
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: 74
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 73
---
# Office 方案部署疑難排解
  本主題包含如何解決部署 Office 解決方案常見問題的相關資訊。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 使用事件檢視器疑難排解 Office 解決方案  
 在安裝或解除安裝 Office 解決方案時，您可以使用 Windows 的事件檢視器查看 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 擷取的錯誤訊息。 您可以使用事件記錄器的這些訊息，解決安裝和部署問題。 如需詳細資訊，請參閱[Office 方案的事件記錄](../vsto/event-logging-for-office-solutions.md)。  
  
## 變更組件名稱會導致衝突  
 如果您在部署了解決方案之後，變更 \[專案設計工具\] 之 \[應用程式\] 頁面中的 \[組件名稱\] 值，發佈工具就會修改安裝套件，變成有一個 Setup.exe 檔案和兩個部署資訊清單。 如果您部署兩個資訊清單檔案，就可能發生下列狀況：  
  
-   如果使用者兩個版本都安裝，應用程式就會載入兩個 VSTO 增益集。  
  
-   如果先安裝了 VSTO 增益集才變更組件名稱，使用者永遠都收不到更新。  
  
 為避免這些狀況，部署解決方案之後，請不要變更解決方案的 \[組件名稱\] 值。  
  
## 檢查更新需要很長的時間  
 Visual Studio 2010 Tools for Office Runtime 提供的登錄項目，讓系統管理員可以設定下載資訊清單和解決方案的逾時值。  
  
#### 設定逾時值  
  
1.  在登錄中，瀏覽至下列機碼：  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\VSTA  
  
2.  在 **AddInTimeout** 子機碼中，將逾時值設定為毫秒。  
  
     如果沒有 **AddInTimeout** 子機碼，請將其建立為 DWORD。  
  
## 無法更新或發佈到網路檔案共用  
 如果解決方案的 Setup.exe 檔案在更新發佈時鎖定在處理序中，網路檔案共用上的 office 解決方案可能會在更新期間顯示誤導的訊息。 訊息內容可能是：「無法將 'setup.exe' 加入 Web。 Web 中已有檔案 'setup.exe'。」  
  
 為防止檔案鎖定，您可以與使用者共用唯讀。 不過，如果文件位於共用，它們對使用者也會變成唯讀。  
  
## 未安裝 Microsoft Office 的必要條件  
 您可以將 .NET Framework、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 和 Office 主要 interop 組件加入安裝套件當做與 Office 解決方案一起部署的必要條件。 如需如何安裝主要 interop 組件的相關資訊，請參閱 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md) 和 [如何：安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)。  
  
## 使用 'Localhost' 發行會導致安裝問題  
 當您使用 "http:\/\/localhost" 當做文件層級解決方案的發佈或安裝位置時，\[發佈精靈\] 不會將字串轉換成實際的電腦名稱。 在這種情況下，解決方案必須安裝在開發電腦上。 為使得部署的方案在開發電腦上使用 IIS，所有的 HTTP\/HTTPS\/FTP 位置請使用完整格式名稱，不要使用 localhost。  
  
## 載入快取的組件，不載入更新的組件  
 當專案輸出路徑位於網路檔案共用時、組件以強式名稱簽署時，以及自訂的組件版本未改變時，Fusion \(.NET Framework 組件載入器\) 會載入組件的快取複本。 如果您更新的組件符合這些條件，因為已載入了快取的複本，所以下次執行專案時，更新就不會出現。  
  
 您可以設定 Visual Studio，每次執行專案時都讓 Fusion 下載組件。  
  
#### 下載組件，不載入快取複本  
  
1.  在功能表列上，選擇 \[專案\]、\[ProjectName 屬性\]。  
  
2.  在 \[應用程式\] 頁面上選擇 \[組件資訊\]。  
  
3.  在第一個 \[組件版本\] 方塊中，輸入星號 \(\*\)，然後選擇 \[確定\] 按鈕。  
  
 變更組件版本之後，您可以繼續以強式名稱簽署組件，Fusion 會載入最新的自訂版本。  
  
## URI 有非 US\-ASCII 字元時安裝失敗  
 當您發佈 Office 解決方案到 HTTP\/HTTPS\/FTP 位置時，路徑不能有不是 US\-ASCII 的任何 Unicode 字元。 這種字元會造成安裝程式的不一致行為。 安裝路徑請使用 US\-ASCII 字元。  
  
## 當您在開發電腦上發佈和安裝解決方案時，系統會提示您手動解除安裝  
 當您建置 Office 解決方案時，建置的版本會自動註冊。 如果先前已在開發電腦發佈和安裝了相同的解決方案，當再次建置、重建或發佈解決方案之後，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會偵測到發佈版本和建置版本的安裝路徑不同。 錯誤訊息顯示：「無法安裝自訂，因為目前安裝了其他版本，而且無法從這個位置進行升級。」 每次重建解決方案都會更新登錄機碼。 因此，您必須先解除安裝舊版再發佈、偵錯或執行新的版本。  
  
 若要防止訊息出現，請在開發電腦上建立另一個使用者帳戶測試部署。 或者，您可以先從電腦的已安裝程式清單中解除安裝版本，再發佈、偵錯或重建解決方案。  
  
## 安裝解決方案時發生無法攔截的例外狀況或找不到方法的錯誤  
 當您開啟部署資訊清單 \(.vsto 檔案\) 安裝 Office 解決方案時， Office 應用程式、文件或活頁簿可能會出現下列狀況的錯誤訊息：  
  
-   找不到方法。  
  
-   MissingMethodException。  
  
-   無法攔截的例外狀況。  
  
 若要避免這些錯誤訊息，請執行安裝程式安裝解決方案。  
  
 當您安裝解決方案卻沒有執行安裝程式時，安裝程式不會檢查或安裝必要條件。 安裝程式會檢查必要條件的正確版本，並視需要加以安裝。  
  
## 建置 InstallShield 限量版專案後，變更增益集的資訊清單登錄機碼  
 資訊清單登錄機碼是 VSTO 增益集安裝程式的一部分，在建置 InstallShield 限量版專案時，有時會從 .vsto 變成 .dll.manifest。  
  
 若要解決這個問題，請在不同的解決方案中建立 InstallShield 限量版專案，或使用 CompanyName.AddinName 當做包含 VSTO 增益集名稱的登錄機碼值。  
  
## Office 解決方案的 ClickOnce 安裝程式不安裝主要 Interop 組件  
 當您執行 ClickOnce 為 Office 解決方案建立的安裝程式時，只有在未安裝任何主要 interop 組件 \(PIA\) 的情況下，Office PIA 的安裝程式才會執行。  
  
 如果安裝程式未正確安裝 PIA，請從安裝目錄執行名為 o2007pia.msi 的安裝程式檔案，手動安裝 PIA。  
  
## 重新安裝 Office 解決方案導致引數超出範圍的例外狀況  
 當您重新安裝 Office 解決方案時，可能會出現 <xref:System.ArgumentOutOfRangeException> 例外狀況及下列錯誤訊息：指定的引數超出有效值的範圍。  
  
 如果安裝位置的 URL 大小寫不同，就會發生這種情況。 例如，如果第一次是從 [http:\/\/fabrikam.com\/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) 安裝 Office 解決方案，然後第二次從 [http:\/\/fabrikam.com\/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto)，就會出現這個錯誤。  
  
 若要防止訊息出現，請在安裝 Office 解決方案時使用相同的大小寫。  
  
## 從 Web 開啟部署資訊清單無法安裝 ClickOnce 解決方案  
 使用者可以從 Web 開啟部署資訊清單，藉以安裝 Office 解決方案。 不過，某些 Internet Information Services \(IIS\) 安裝會封鎖副檔名為 .vsto 的檔案。 您必須先在 IIS 中定義 MIME 類型，再用它部署 Office 解決方案。  
  
 如需如何在 IIS 6 中定義 MIME 類型的相關資訊，請參閱[設定 MIME 類型 \(IIS 6.0\)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true)。  
  
 如需如何在 IIS 7 中定義 MIME 類型的相關資訊，請參閱[加入 MIME 類型 \(IIS 7\)](http://technet.microsoft.com/library/cc725608(WS.10).aspx)。  
  
 將副檔名設為 **.vsto**，MIME 類型設為 **application\/x\-ms\-vsto**。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  