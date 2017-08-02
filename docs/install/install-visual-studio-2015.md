---
title: "安裝 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.about"
helpviewer_keywords: 
  - "Visual Studio，安裝"
  - "安裝 Visual Studio"
  - "伺服器安裝 [Visual Studio]"
  - "安裝 [Visual Studio]"
  - "安裝 Visual Studio"
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 177
caps.handback.revision: 150
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 安裝 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此頁面包含了可協助您安裝 Visual Studio 2015 的詳細資訊，Visual Studio 2015 是適用於開發人員的產能工具整合式套件。 其中也包含連結，協助您快速取得[功能](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx)、[版本](http://go.microsoft.com/fwlink/?LinkID=242142)、[系統需求](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)、[下載](http://go.microsoft.com/fwlink/?LinkId=517106)，以及其他項目的詳細資訊。  
  
> [!TIP]
>  若要檢視舊版 Visual Studio 的安裝資訊，請按一下這個頁面頂端的 \[其他版本\] 連結。  
  
## 快速連結  
 在我們深入了解詳細資料之前，以下是最常使用的連結清單。  
  
|功能|  
|--------|  
|若要深入了解 Visual Studio 2015 中新增或更新的功能，請參閱 [Visual Studio 2015 RTM](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx) 和 [Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs) 的版本資訊。|  
|若要了解每一個版本的 Visual Studio 2015 有哪些可用功能，請參閱[比較 Visual Studio 產品](http://go.microsoft.com/fwlink/?LinkID=242142)頁面。|  
|若要檢視每個版本 Visual Studio 2015 的系統需求，請參閱 [Visual Studio 2015 相容性](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)頁面。|  
|若要安裝 Visual Studio 2015，請從 [Visual Studio 下載](http://go.microsoft.com/fwlink/?LinkId=517106)中下載，或使用盒裝產品的安裝媒體。|  
|若要找出產品金鑰，請參閱[如何：找出 Visual Studio 產品金鑰](../install/how-to-locate-the-visual-studio-product-key.md)主題。|  
|若要了解個人或企業客戶的授權選項，請參閱 [Visual Studio 和 MSDN 授權](https://www.microsoft.com/download/details.aspx?id=13350)白皮書。|  
  
##  <a name="custom"></a> 預設值與自訂設定  
 當您安裝 Visual Studio 2015 時，您可以包含或排除您日常使用的元件。 這表示預設安裝通常會比自訂安裝更小，而且安裝速度更快。 這也意謂著在舊版中許多預設安裝的元件，在此版本中已改為您必須明確選取的「自訂」元件。  
  
 ![Visual Studio 2015 的 &#91;安裝&#93; 對話方塊](~/ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
 自訂元件包括 Visual C\+\+、Visual F \#、SQL Server Data Tools、跨平台行動工具和 SDK 以及協力廠商 SDK 和擴充功能。 如果您沒有在初始安裝期間選取任何自訂元件，仍可於稍後安裝。  
  
> [!NOTE]
>  自訂安裝會自動包含預設安裝中的元件。  
  
 自訂元件的完整清單如下所示：  
  
-   **程式語言**  
  
    -   Visual C\+\+ 編譯器、程式庫和工具  
  
    -   Visual F\#  
  
    -   Python Tools for Visual Studio  
  
-   **Windows 和 Web 開發**  
  
    -   ClickOnce 發行工具  
  
    -   Microsoft SQL Server Data Tools  
  
    -   Microsoft Web 開發人員工具  
  
    -   PowerShell Tools for Visual Studio  
  
    -   Silverlight 開發套件  
  
    -   通用 Windows App 開發工具  
  
    -   Windows 10 工具和 SDK  
  
    -   Windows 8.1 和 Windows Phone 8.0 工具  
  
    -   Windows 8.1 工具和 SDK  
  
-   **跨平台行動開發**  
  
    -   Xamarin \(C\#\/.NET\)  
  
    -   Apache Cordova \(HTML\/JavaScript\)  
  
    -   適用於 iOS \/ Android 的 Visual C\+\+ 行動開發  
  
-   **通用工具和 SDK**  
  
    -   Android 原生開發套件 \(R10E，32 位元\)  
  
    -   Android SDK  
  
    -   Android SDK 安裝程式 \(API 層級 19 和 21\)  
  
    -   Android SDK 安裝程式 \(API 層級 22\)  
  
    -   Apache Ant \(1.9.3\)  
  
    -   Java SE 開發套件 \(7.0.550.13\)  
  
    -   Joyent Node.js  
  
-   **通用工具**  
  
    -   適用於 Windows 的 Git  
  
    -   適用於 Visual Studio 的 GitHub 擴充功能  
  
    -   Visual Studio 擴充性工具  
  
##  <a name="installing"></a> 安裝 Visual Studio  
 您必須擁有系統管理員認證才能安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 不過，在安裝之後，您不需要它們也可使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 您的本機系統管理員帳戶必須啟用下列權限，才能安裝 Visual Studio 中的所有項目。  
  
|本機原則物件的顯示名稱|使用者權限|  
|-----------------|-----------|  
|備份檔案和目錄|SeBackupPrivilege|  
|偵錯程式|SeDebugPrivilege|  
|管理稽核和安全性記錄檔|SeSecurityPrivilege|  
  
 如需本機系統管理員帳戶需求的詳細資訊，請參閱知識庫文件[如果安裝帳戶並沒有特定使用者權限，SQL Server 安裝會失敗](https://support.microsoft.com/en-us/kb/2000257)。  
  
###  <a name="BKMK_Media"></a> 使用安裝媒體進行安裝  
  
-   若要安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，請在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝媒體的根目錄中，針對您想要的版本來執行安裝檔案：  
  
    |版本|安裝檔案|  
    |--------|----------|  
    |Visual Studio 企業版|vs\_enterprise.exe|  
    |Visual Studio Professional|vs\_professional.exe|  
    |Visual Studio 社群|vs\_community.exe|  
  
###  <a name="BKMK_Website"></a> 藉由從產品網站下載進行安裝  
  
-   請前往 VisualStudio.com 網站，造訪 [Visual Studio 下載](http://go.microsoft.com/fwlink/?LinkId=517106)。  
  
###  <a name="BKMK_Offline"></a> 下載 Visual Studio 進行離線安裝  
 在大部分情況下，您可以毫無問題的從下載網站安裝 Visual Studio。 不過，在某些情況下，您可能要先下載所有更新封裝，然後再安裝 \(例如安裝在多部電腦上或在離線電腦上\)。 下列步驟說明如何下載進行離線安裝需要的所有更新封裝。  
  
1.  從 MSDN 網站下載更新可執行檔至您的檔案系統位置之後，從命令提示字元執行下列命令：`<executable name> /layout`。  
  
     這個命令會下載進行安裝的所有封裝。  
  
     您可以使用 `/layout` 參數下載幾乎所有核心安裝封裝，而不只是適用於下載電腦的封裝。 這種方法提供您在任何位置執行這個更新時需要的所有檔案，並有助於您安裝一開始未安裝的元件。  
  
2.  在您執行命令之後，應該會提示您輸入下載位置。 輸入位置，然後選擇 \[下載\]。  
  
3.  封裝順利下載完成時，您應該會看到 Visual Studio 螢幕顯示**設定成功！**。**已成功取得所有指定元件。**  
  
4.  在您指定的檔案位置中，尋找可執行檔和封裝資料夾。 這就是複製到共用位置或安裝媒體所需做的一切動作。  
  
    > [!CAUTION]
    >  Android SDK 目前尚不支援離線安裝體驗。 如果您將 Android SDK 安裝程式的項目安裝在未連線至網際網路的電腦，安裝可能會失敗。  
  
5.  您現在可以從檔案位置或安裝媒體上執行安裝。  
  
###  <a name="BKMK_Virtualized"></a> 在虛擬化的環境中安裝 Visual Studio  
 **HYPER\-V 的視訊問題**  
  
 如果 Windows Server 2008 R2 是在啟用 Hyper\-V 的情況下使用加速圖形卡來執行，您可能會感受到系統速度變慢。  
  
 如需詳細資訊，請參閱 Microsoft 網站的下列網頁：[當 Windows Server 2008 或 Windows Server 2008 R2 電腦已啟用 Hyper\-V 角色且有安裝加速顯示卡時，視訊效能可能會降低](http://go.microsoft.com/fwlink/?LinkID=231084)。  
  
 **使用 HYPER\-V 模擬裝置**  
  
 當您在實際的硬體上安裝 Visual Studio 2015，但沒有虛擬化時，您可以使用 HYPER\-V 選擇能模擬 Windows 和 Android 裝置的功能。 當您安裝到 HYPER\-V 時，將無法模擬 Windows 或 Android 裝置。 這是因為模擬器本身是虛擬機器，您目前不能在另一個 VM 內裝載 VM。 因應措施是使用實際的 Windows 或 Android 裝置，您可以直接在上面部署和偵錯應用程式。  
  
## 使用命令列參數  
 執行安裝應用程式時，您可以使用下列命令列參數 \(不區分大小寫\)。  
  
|參數|描述|  
|--------|--------|  
|**\/?**<br /><br /> **\/help**<br /><br /> **\/h**|顯示命令列參數。|  
|**\/AddRemoveFeatures**|指定要加入哪些功能或從已安裝的產品移除哪些功能。|  
|**\/AdminFile** *AdminDeployment.xml*|使用您指定用於管理安裝的資料檔案，安裝 Visual Studio。|  
|**\/CEIPConsent**|依照產品隱私權原則，同意資訊收集以改善客戶經驗。|  
|**\/ChainingPackage** *套件組合名稱*|指定哪一個套件組合要鏈結這個套件組合。 這也可用來指定客戶經驗改進的群組。|  
|**\/CreateAdminFile \<filename\>**|指定要搭配 \/AdminFile 使用之控制檔的建立位置|  
|**\/CustomInstallPath** *安裝目錄*|將所有可重定目標的封裝安裝在您指定的目錄中。|  
|**\/ForceRestart**|一律在安裝之後重新啟動電腦。|  
|**\/full**|安裝所有產品功能。|  
|**\/InstallSelectableItems \<item name 1\>\[;\<item name 2\>\]**|樹狀結構項目的選取清單，確認安裝精靈的選取畫面。|  
|**\/l**<br /><br /> **\/Log** *檔案名稱*|指定記錄檔的位置。|  
|**\/layout** *目錄*|將安裝媒體上的檔案複製到您指定的目錄。|  
|**\/NoCacheOnlyMode**|防止封裝快取的預先填入。|  
|**\/NoRefresh**|不要檢查本產品較新版本所必需或建議的更新版本。|  
|**\/norestart**|在安裝期間或之後，防止安裝應用程式重新啟動電腦。 如需尋找傳回碼，請參閱 [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)的＜傳回碼＞一節。|  
|**\/noweb**|防止從網際網路進行安裝。|  
|**\/OverrideFeedUri \<path to feed file\>**|本機的路徑，為描述軟體項目的外部輸入。|  
|**\/ProductKey**<br /><br /> *ProductKey*|設定不包含虛線和不超過 25 個字元的自訂產品金鑰。|  
|**\/PromptRestart**|在重新啟動電腦之前提示使用者。|  
|**\/q**<br /><br /> **\/quiet**<br /><br /> **\/s**<br /><br /> **\/silent**|隱藏安裝應用程式的使用者介面 \(UI\)。 如果 Visual Studio 已安裝，而且除了這個參數之外，您沒有指定其他參數，則安裝應用程式會在維護模式下執行。|  
|**\/qb**<br /><br /> **\/passive**|顯示進度，但不等候使用者輸入。|  
|**\/repair**|修復 Visual Studio。|  
|**\/SuppressRefreshPrompt**|不要在安裝精靈中顯示可用更新對話方塊，如此一來，安裝精靈將會自動接受任何必要或建議的更新版本。|  
|**\/u**<br /><br /> **\/Uninstall**|解除安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|  
|**\/Uninstall \/Force**<br /><br /> **\/u \/force**|解除安裝 Visual Studio 以及與其他產品共用的所有功能。 **Warning:**  如果您使用這個參數，在同一部電腦上安裝的其他產品可能會無法正確運作。|  
  
 當從命令列執行安裝程式，您會想要擷取和處理傳回碼，以獲得更佳的命令列體驗。  如需詳細資訊，請參閱 [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)。  
  
##  <a name="troubleshooting"></a> 安裝疑難排解  
 請使用下列資源來取得設定及安裝問題的協助：  
  
-   [Visual Studio 安裝程式和安裝](http://go.microsoft.com/fwlink/?LinkID=151190)論壇。 在 Visual Studio 社群中，檢閱其他人提供的問題和解答。 如果您找不到所需的資訊，請詢問您自己的問題。  
  
-   [Microsoft Visual Studio 支援](http://go.microsoft.com/fwlink/?LinkID=251019)網站。 閱讀知識庫 \(KB\) 文章，並了解如何連絡 Microsoft 技術支援以取得 Visual Studio 安裝問題的相關資訊。  
  
-   針對各種版本的 Visual Studio 2015，您可使用 Connect 網站來報告問題，網址為 [https:\/\/connect.microsoft.com\/visualstudio](https://connect.microsoft.com/visualstudio)。  
  
     如果您的問題包含安裝記錄檔將再好不過了。 您可以使用 Microsoft Visual Studio 和 .NET Framework 記錄收集工具準備問題報告的記錄，如下列步驟所述。  
  
    1.  從 [http:\/\/aka.ms\/vscollect](http://aka.ms/vscollect) 下載安裝診斷工具  
  
    2.  從提升權限的命令提示字元中，執行 collect.exe 程式。  
  
    3.  collect.exe 程式完成之後，從暫存目錄擷取 vslogs.cab 檔案，並上傳至問題報告。  
  
##  <a name="enterprise"></a> 企業網路部署  
 如需如何透過網路部署 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的詳細資訊，請參閱 [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)。  
  
##  <a name="afterInstalling"></a> 安裝 Visual Studio 之後  
 完成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝之後，建議您註冊產品。  
  
###  <a name="register"></a> 註冊 Visual Studio  
  
##### 若要註冊 Visual Studio  
  
1.  在功能表列上，選取 \[說明\]、\[關於\]。  
  
     \[關於\] 對話方塊會顯示產品識別碼 \(PID\)。 您將需要 PID 和 Windows 帳戶認證 \(例如 Hotmail 或 Outlook.com 電子郵件地址和密碼\) 以註冊產品。  
  
2.  在功能表列上，選擇 \[說明\]、\[註冊產品\]。  
  
###  <a name="helpContent"></a> 安裝離線說明內容  
 安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之後，您可以下載其他的說明內容，以便可以離線使用。  
  
##### 安裝或解除安裝說明內容  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 功能表列上，依序選擇 \[說明\]、\[加入和移除說明內容\]。  
  
2.  在 \[Microsoft 說明檢視器\] 的 \[管理內容\] 索引標籤上，選取適用於您說明內容的安裝來源。  
  
3.  如果您要尋找特定的說明集合，請在 \[搜尋\] 文字方塊中輸入名稱或關鍵字，然後按 Enter。  
  
4.  在您想要的說明集合名稱旁邊，選擇 \[加入\] 或 \[移除\] 連結。  
  
5.  選擇 \[更新\] 按鈕。  
  
 如需離線說明的詳細資訊，請參閱 [Microsoft 說明檢視器 2.2 說明](../ide/microsoft-help-viewer.md)  
  
###  <a name="repair"></a> 修復 Visual Studio  
  
##### 若要修復 Visual Studio  
  
1.  在 \[控制台\] 的 \[程式和功能\] 頁面上，選取要修復的產品版本，然後選擇 \[變更\]。  
  
2.  在安裝精靈中，依序選擇 \[修復\]、\[下一步\]，然後依照其餘指示進行。  
  
##### 若要以無訊息或被動模式修復 Visual Studio \(亦即從來源修復\)  
  
1.  在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。  
  
2.  輸入下列參數：  
  
     *DVDRoot* \\\<安裝檔案\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/Repair  
  
###  <a name="optionalComponents"></a> 安裝可選取的項目  
  
##### 若要安裝可選取的項目  
  
1.  在 \[控制台\] 的 \[程式和功能\] 頁面上，選擇要在其中加入一個或多個元件的產品版本，然後選擇 \[變更\]。  
  
2.  在安裝精靈中，選擇 \[修改\]，然後選擇您要安裝的元件。  
  
3.  選擇 \[下一步\]，然後依照其餘指示進行。  
  
###  <a name="serviceReleases"></a> 檢查版本更新服務與產品更新  
 從舊版升級時，Visual Studio 不會自動升級擴充功能，因為並非所有擴充功能都相容。 您必須從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=178891)或軟體發行者重新安裝擴充功能。  
  
##### 自動檢查版本更新服務  
  
1.  在功能表列上選擇 \[工具\]、\[選項\]。  
  
2.  在 \[選項\] 對話方塊中，展開 \[環境\]，然後選取 \[擴充功能和更新\]。 確定已選取 \[自動檢查更新\] 核取方塊，然後選擇 \[確定\]。  
  
##  <a name="uninstalling"></a> 解除安裝 Visual Studio  
 請使用下列程序解除安裝 Visual Studio 2015。  
  
#### 若要解除安裝 Visual Studio  
  
1.  在 \[控制台\] 的 \[程式和功能\] 頁面上，選取要解除安裝的產品版本，然後選擇 \[變更\]。  
  
2.  在安裝精靈中，依序選擇 \[解除安裝\]、\[是\]，然後依照精靈中的其餘指示進行。  
  
#### 若要以無訊息或被動模式解除安裝 Visual Studio \(亦即從來源解除安裝\)  
  
1.  在安裝 Visual Studio 的電腦上，開啟 Windows 命令提示字元。  
  
2.  輸入下列參數：  
  
     *DVDRoot* \\\<安裝檔案\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/uninstall  
  
 如果您無法使用解除安裝公用程式來解除安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，可以先移除 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然後再移除相關的元件，藉此執行手動解除安裝。 如需詳細資訊，請參閱 Microsoft 知識庫 \(KB\) 的[如何解除安裝 Visual Studio](https://support.microsoft.com/en-us/kb/2771441) 一文，或 Microsoft 伺服器及工具部落格網站上的[移除 Visual Studio 解除安裝之後遺留的元件](http://blogs.msdn.com/b/heaths/archive/2015/07/17/removing-visual-studio-components-left-behind-after-an-uninstall.aspx)一文。  
  
##  <a name="relatedTopics"></a> 相關主題  
  
|標題|描述|  
|--------|--------|  
|[並存安裝 Visual Studio 版本](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)|提供如何在同一部電腦上安裝多個 Visual Studio 版本的相關資訊。|  
|[Visual Studio 影像庫](../designers/the-visual-studio-image-library.md)|提供如何安裝可在 Visual Studio 應用程式中使用之圖形的相關資訊。|  
|[Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)|提供 Visual Studio 部署選項的相關資訊。|  
|[安裝多個語言版本的 Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)|提供如何安裝 Visual Studio 各種語言版本的相關資訊。|  
|[如何：找出 Visual Studio 產品金鑰](../install/how-to-locate-the-visual-studio-product-key.md)|提供如何找出 Visual Studio 安裝之產品金鑰的相關資訊。|  
|[快速入門](../ide/get-started-developing-with-visual-studio.md)|連結至可協助您有效使用 Visual Studio 的文件。|  
  
## 請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)