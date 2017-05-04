---
title: "對 SharePoint 方案進行偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 偵錯"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 對 SharePoint 方案進行偵錯
  您可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具對 SharePoint 方案進行偵錯。  當您開始偵錯時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將專案檔部署至 SharePoint 伺服器，然後在 Web 瀏覽器中開啟 SharePoint 網站的執行個體。  下列章節說明如何在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中對 SharePoint 應用程式進行偵錯。  
  
-   [啟用偵錯](#EnableDebug)  
  
-   [F5 偵錯和部署程序](#Deployment)  
  
-   [SharePoint 專案功能](#Features)  
  
-   [對工作流程進行偵錯](#Workflow)  
  
-   [對功能事件接收器進行偵錯](#FeatureEvents)  
  
-   [啟用增強型偵錯資訊](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> 啟用偵錯  
 當您一開始在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中對 SharePoint 方案進行偵錯時，會出現對話方塊，提醒您 web.config 檔未設定為啟用偵錯 \(安裝 SharePoint 伺服器時，便會建立 web.config 檔。  如需詳細資訊，請參閱 [Web.config 檔案](http://go.microsoft.com/fwlink/?LinkID=149266)。此對話方塊提供選項，讓您選擇執行專案但不偵錯，還是修改 web.config 檔以啟用偵錯。  選取第一個選項，則專案會正常執行。  選取第二個選項，則 web.config 檔會設定為：  
  
-   開啟呼叫堆疊 \(`CallStack="true"`\)  
  
-   停用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自訂錯誤 \(`<customErrors mode="Off" />`\)  
  
-   啟用編譯偵錯 \(`<compilation debug="true">`\)  
  
 產生的 web.config 檔如下所示：  
  
```  
  
<configuration>  
    ...  
    <SharePoint>  
        <SafeMode MaxControls="200"  
            CallStack="true"  
            DirectFileDependencies="10"  
            TotalFileDependencies="50"  
            AllowPageLevelTrace="false">  
            ...  
        </SafeMode>  
    ...  
    </SharePoint>  
    <system.web>  
        ...  
        <customErrors mode="Off" />  
        ...  
        <compilation debug="true">  
        ...  
        </compilation>  
        ...  
    </system.web>  
    ...  
</configuration>  
```  
  
 若要回復變更並停用偵錯，請變更 web.config 檔的下列 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]：  
  
-   關閉呼叫堆疊 \(`CallStack="false"`\)  
  
-   啟用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的自訂錯誤 \(`<customErrors mode="On" />`\)  
  
-   停用編譯偵錯 \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> F5 偵錯和部署程序  
 當您在偵錯模式中執行 SharePoint 專案時，SharePoint 部署流程會執行下列工作：  
  
1.  執行可自訂的預先部署命令。  
  
2.  使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 命令建立 Web 方案套件 \(.wsp\) 檔。  .wsp 檔包含所有必要的檔案和功能。  如需詳細資訊，請參閱[方案概觀](http://go.microsoft.com/fwlink/?LinkID=128154)。  
  
3.  如果 SharePoint 方案是陣列方案，會針對指定的網站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 回收 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區。  此步驟會釋放 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 背景工作處理序鎖定的檔案。  
  
4.  如果舊版套件已經存在，則會撤銷 .wsp 檔中的舊版功能和檔案。  此步驟會停用功能、解除安裝方案套件，然後刪除 SharePoint 伺服器上的方案套件。  
  
5.  安裝 .wsp 檔中功能和檔案的目前版本。  此步驟會在 SharePoint 伺服器上加入並安裝方案。  
  
6.  針對工作流程，安裝工作流程組件。  您可以使用 *Assembly Location* 屬性變更組件的位置。  
  
7.  如果範圍為 \[網站\] 或 \[Web\]，會在 SharePoint 中啟動專案的功能。  \[伺服器陣列\] 和 \[WebApplication\] 範圍中的功能則不會啟動。  
  
8.  針對工作流程，將工作流程與您在 \[**SharePoint 自訂精靈**\] 中選取的程式庫、清單或網站產生關聯。  
  
    > [!NOTE]  
    >  只有在您在精靈中選取 \[**自動與工作流程關聯**\] 時，才會建立關聯。  
  
9. 執行可自訂的部署後命令。  
  
10. 將[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具附加至 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 處理序（w3wp.exe ）。  如果專案類型可讓您變更*Sandboxed Solution* 屬性，而且其值設定為**true**，則偵錯工具會附加至不同的處理序 \(SPUCWorkerProcess.exe\)。  如需詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
11. 如果 SharePoint 方案是陣列方案，會啟動 JavaScript 偵錯工具。  
  
12. 在 Web 瀏覽器中顯示適當的程式庫、清單或網站頁面。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在每項工作完成後，於 \[輸出\] 視窗中顯示狀態訊息。  如果工作無法完成，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在 \[錯誤清單\] 視窗中顯示錯誤訊息。  
  
##  <a name="Features"></a> SharePoint 專案功能  
 功能 \(Feature\) 是指一組可攜的模組化功能 \(Functionality\) 單元，可使用網站定義簡化修改網站的作業。  它也是 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\) 項目的套件，可針對特定範圍啟動，並且協助使用者完成特定目標或工作。  範本會部署為功能。  
  
 當您在偵錯模式執行專案時，部署程序會在「*功能*」\(Feature\) 目錄中建立資料夾，這個目錄的位置是 %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES。  功能名稱的格式為*project name*\_Feature*x*，例如 TestProject\_Feature1。  
  
 feature 目錄中的方案資料夾包含「*功能定義*」\(Feature Definition\) 檔和「*工作流程定義*」\(Workflow Definition\) 檔。  功能定義檔 \(Feature.xml\) 會描述專案功能中的檔案，專案定義檔 \(Elements.xml\) 則會描述專案範本。  Elements.xml 可以在 \[**方案總管**\] 中找到，但 Feature.xml 則在方案套件建立時產生。  如需這些檔案的詳細資訊，請參閱 [SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
##  <a name="Workflow"></a> 對工作流程進行偵錯  
 當您對工作流程專案進行偵錯時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將工作流程範本加入至程式庫或清單 \(視範本類型而定\)。  您接著可以加入或更新項目來手動啟動工作流程範本，  再使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 對工作流程進行偵錯。  
  
> [!NOTE]  
>  如果您將參考加入至其他組件，請確定這些組件安裝在全域組件快取 \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) 中。  否則工作流程方案將會失敗。  如需安裝組件的詳細資訊，請參閱[手動開始文件或項目的工作流程](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
 不過，部署程序不會啟動工作流程。  您必須從 SharePoint 網站啟動工作流程。  您也可以使用用戶端應用程式 \(如 Microsoft Office Word 2010\)，或是使用其他伺服器端程式碼啟動工作流程。  請使用 \[**SharePoint 自訂精靈**\] 內指定的其中一個方法。  
  
 例如，如果您指定可以手動啟動工作流程，請直接從文件庫或清單中的項目啟動工作流程。  如需手動啟動工作流程的詳細資訊，請參閱[手動啟動文件項目的工作流程](http://go.microsoft.com/fwlink/?LinkID=79938)。  
  
##  <a name="FeatureEvents"></a> 對功能事件接收器進行偵錯  
 執行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 應用程式時，它在 SharePoint 伺服器上的功能預設會自動啟動供您使用。  不過，當您對功能事件接收器進行偵錯時，這會造成問題，因為當功能由 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 啟動時，它會在與偵錯工具不同的處理序中執行。  這表示部分偵錯功能 \(如中斷點\) 將無法正常運作。  
  
 若要在 SharePoint 中停用自動啟動功能並允許對功能事件接收器正常偵錯，請在偵錯之前，將專案的 \[**現用部署組態**\] 屬性值設定為 \[**不啟動**\]。  接著，在您開始使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 進行 SharePoint 應用程式偵錯時，請在 SharePoint 中手動開啟功能。  若要這麼做，請在 SharePoint 中的 \[**網站動作**\] 功能表上按一下 \[**網站設定**\]，然後選擇 \[**管理網站功能**\] 連結，再按一下功能旁的 \[**啟動**\] 按鈕，並按照一般方式繼續偵錯。  
  
##  <a name="EnhancedDebug"></a> 啟用增強型偵錯資訊  
 由於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 處理序 \(devenv.exe\)、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 主機處理序 \(vssphost4.exe\)、SharePoint 和 WCF 層之間的互動有時候相當複雜，要診斷建置、部署和執行其他作業時發生的錯誤可能不容易。  為協助解析這類錯誤，您可以啟用增強型偵錯資訊。  若要這麼做，請至 Windows 登錄中的下列登錄機碼：  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 如果「EnableDiagnostics」 **REG\_DWORD** 值不存在，請手動建立它。  設定「EnableDiagnostics」值為「1. "  
  
 將此機碼值設定為 1 後，每當在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中執行時發生專案系統錯誤，堆疊追蹤資訊就會顯示在 \[**輸出**\] 視窗中。  若要停用增強型偵錯資訊，請將 EnableDiagnostics 值設回 0 或刪除值。  
  
 如需其他 SharePoint 登錄機碼的詳細資訊，請參閱[Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  