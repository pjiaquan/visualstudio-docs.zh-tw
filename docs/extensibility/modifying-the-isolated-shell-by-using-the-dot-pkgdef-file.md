---
title: "使用修改獨立的 Shell。Pkgdef 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 41e91983aaf236682b4ce723143f4053b5189547
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>使用修改獨立的 Shell。Pkgdef 檔案
.Pkgdef 檔支援可讓您自訂獨立的 shell 應用程式的設定。 它會指定應用程式的電腦上安裝並啟動應用程式時，Visual Studio shell 所參考之時所建立的值。 設定會組織適用的登錄機碼為基礎的檔案中。  
  
> [!WARNING]
>  請注意，Visual Studio 啟動時不會掃描 VSPackage 的.vsixmanifest 檔案中未宣告的.pkgdef 檔。  
  
 .Pkgdef 檔包含每個識別的索引鍵，或是區段`[$RootKey$]`或`[$RootKey$\`*子機碼*`]`，其中 $RootKey$ 是應用程式的根目錄機碼。  
  
 每一個區段包含具有下列格式的名稱/值組︰ `"` *ValueName*`"=`*值*。  
  
 值為字串，括以引號括住或 32 位元整數，表示為 dword。 值具有下列限制︰  
  
-   所有的 dword 值是十六進位格式，例如`dword:00000001`。  
  
     布林值，1 表示 true，而 0 表示 false。  
  
-   所有的 GUID 字串是以登錄格式，例如`"{00000000-0000-0000-0000-000000000000}"`。  
  
-   所有可當地語系化的資源識別項使用表單 」 @*resourceID*"或"#*resourceID*」，其中*resourceID*是應用程式 UI 封裝中的資源識別碼，例如`"@102"`。 應用程式 UI 封裝是封裝所參考的 AppLocalizationPackage 設定。  
  
 例如：  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 您可以將註解加入.pkgdef 檔。 單行註解會有兩個斜線為前兩個字元。  
  
 如需替代字串的清單，請參閱[中使用的替代字串。Pkgdef 和。Pkgundef 檔案](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
 下列章節說明影響行為的 Visual Studio shell 隔離模式中的特定登錄值。 您也可以定義應用程式的其他登錄值，這個檔案中。  
  
> [!NOTE]
>  如果.pkgdef 檔中未提供的設定，然後才進行登錄中沒有對應的項目。  
  
## <a name="settings"></a>設定  
 下表說明 [$RootKey$] 底下定義的值。  
  
|名稱|類型|值|  
|----------|----------|-----------|  
|AddinsAllowed|dword|如果可以載入增益集，則為 true否則為 false。<br /><br /> 預設值為 true。|  
|AllowsDroppedFilesOnMainWindow|dword|如果主視窗可以接受已卸除的檔案，則為 true否則為 false。 藉由開啟檔案放在主視窗<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 這相當於使用開啟的文件**開啟**命令**檔案**應用程式中的功能表。<br /><br /> 預設值為 true。|  
|AppIcon|字串|程式圖示的完整路徑。 這個圖示會出現在標題列左側的 應用程式名稱。<br /><br /> 預設值是"$RootFolder$\\*solutionName*.ico 」，其中*solutionName*是應用程式方案檔的名稱。|  
|AppLocalizationPackage|字串|包含應用程式的 UI 附屬組件的 VSPackage 的 GUID。 此 VSPackage 包含.vsct 檔的編譯的版本，而且可以包含其他當地語系化的字串。 可以啟用或停用變更 UI 專案.vsct 檔中的設定的功能集和功能表命令的群組。<br /><br /> 預設值是"{*vsUiPackageGuid*}"，其中*vsUiPackageGuid*是指派給應用程式 UI 封裝的 GUID。|  
|應用程式名稱|字串|應用程式的名稱。 應用程式視窗的標題列中出現的名稱。<br /><br /> 預設值是應用程式方案檔的名稱。|  
|CommandLineLogo|字串|在主控台視窗中執行應用程式時的橫幅文字。 這個設定會影響支援命令列建置作業的應用程式。<br /><br /> 預設值是"*companyName**solutionName* 1.0 版。 」，其中*companyName*是安裝 Windows 時，所提供的公司名稱和*solutionName*是應用程式方案檔的名稱。|  
|DefaultDebugEngine|字串|預設 GUID 偵錯引擎使用應用程式。<br /><br /> 注意︰ 空的 GUID （全部為零） 表示應用程式不會指定預設偵錯引擎。 這可讓偵錯工具來選取要使用的偵錯引擎。<br /><br /> 預設值是"{00000000-0000-0000-0000-000000000000}"。|  
|DefaultHomePage|字串|內部的網頁瀏覽器視窗的預設首頁 URL。<br /><br /> 如果**首頁**選項可在應用程式，則此設定也會影響選項的預設狀態。 如需詳細資訊，請參閱[Web 瀏覽器中，環境中，[選項] 對話方塊](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 預設值是 Windows 安裝時所提供的公司的 URL。|  
|DefaultProjectsLocation|字串|預設的專案資料夾的完整路徑。 例如：<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> 如果**Visual Studio 專案位置**選項可在應用程式，則此設定也會影響選項的預設狀態。 如需詳細資訊，請參閱[NIB︰ 一般、 專案和方案、 選項對話方塊](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 預設值是"$MyDocuments$\\*solutionName*」，其中*solutionName*是應用程式方案檔的名稱。|  
|DefaultSearchPage|字串|內部的網頁瀏覽器視窗的預設搜尋網頁 URL。<br /><br /> 如果**搜尋網頁**選項可在應用程式，則此設定也會影響選項的預設狀態。 如需詳細資訊，請參閱[Web 瀏覽器中，環境中，[選項] 對話方塊](../ide/reference/web-browser-environment-options-dialog-box.md)。<br /><br /> 預設值是 「 http://search.live.com 」。|  
|DefaultUserFilesFolderRoot|字串|使用者 資料夾中，相對於目前的使用者名稱的我的文件 資料夾。<br /><br /> 預設值是應用程式方案檔的名稱。|  
|DisableOutputWindow|dword|指出是否獨立的 shell 應該將 [輸出] 視窗，因為已停用。<br /><br /> 如果此值設為 true，Visual Studio 不會顯示方案建置管理員輸出，在**輸出**視窗，並且隱藏**建置開始時顯示輸出視窗**中核取方塊**專案和方案**類別目錄中的**選項**對話方塊。<br /><br /> 預設值為 false。|  
|HideMiscellaneousFilesByDefault|dword|如果為 true，則隱藏**其他檔案**資料夾中的預設**方案總管 中**; 否則為 false。<br /><br /> 如果**方案總管 中的顯示其他檔案**選項可在應用程式，則此設定也會影響選項的預設狀態。 如需詳細資訊，請參閱[選項對話方塊、 環境、 文件](../ide/reference/documents-environment-options-dialog-box.md)。<br /><br /> 預設值為 false。|  
|HideSolutionConcept|dword|建立所有獨立的專案和專案依預設，隱藏的方案和獨立專案與方案相關的命令，則為 true否則為 false。<br /><br /> 如果**一律顯示方案**選項可在應用程式，則此設定也會影響選項的預設狀態。 如需詳細資訊，請參閱[NIB︰ 一般、 專案和方案、 選項對話方塊](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。<br /><br /> 預設值為 false。|  
|NewProjDlgInstalledTemplatesHdr|字串|在 Visual Studio 快速範本標頭名稱**範本**清單中**新的專案**對話方塊。 這是字串或載入的應用程式 UI 封裝的可當地語系化的資源識別碼。<br /><br /> 預設值是"*solutionName*已安裝的範本 」，其中*solutionName*是應用程式方案檔的名稱。|  
|NewProjDlgSlnTreeNodeTitle|字串|名稱**Visual Studio 方案**節點**專案類型**樹狀目錄中**新的專案**對話方塊。 這是字串或載入的應用程式 UI 封裝的可當地語系化的資源識別碼。<br /><br /> 預設值是"*solutionName*已安裝的範本 」，其中*solutionName*是應用程式方案檔的名稱。|  
|SolutionFileCreatorIdentifier|字串|應用程式識別項，會出現在應用程式所產生的方案檔中的第二行。 這一行會顯示建立檔案的應用程式。 依照慣例，這個值會包含名稱的應用程式和應用程式版本號碼。 例如：<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> VSLauncher.exe 程式，也就是開啟 Visual Studio 方案檔的預設程式，會使用第二個此行判斷新版 Visual Studio 中開啟方案檔。 應用程式需要它自己的啟動程式來處理其相關聯的方案檔。 啟動器無法也使用此第二行方案檔來判斷哪個版本的應用程式中開啟方案中。<br /><br /> 注意︰ Visual Studio VSLauncher.exe 程式不會處理所建立的應用程式獨立的 shell 的.sln 檔案。<br /><br /> 預設值是"*solutionName* 10.00 」 的格式版本 方案檔案，其中*solutionName*是應用程式方案檔的名稱。|  
|SolutionFileExt|字串|方案檔名的副檔名為應用程式的。 我們建議您選擇唯一的檔名的副檔名 (not.sln)。<br /><br /> 預設值是"*solutionName*_sln 」，其中*solutionName*是應用程式方案檔的名稱。|  
|SplashScreenBitmap|字串|應用程式啟動顯示畫面的點陣圖檔案的完整路徑。<br /><br /> 預設值是 「 $RootFolder$\Splash.bmp 」。|  
|ThisVersionDTECLSID|字串|應用程式的自動化物件類別識別項 (CLSID)。<br /><br /> 應用程式自動化物件是在 Visual Studio shell automation 模型和實作應用程式的最上層物件<xref:EnvDTE._DTE?displayProperty=fullName>介面。</xref:EnvDTE._DTE?displayProperty=fullName><br /><br /> 如果應用程式自動化物件正確登錄 HKEY_CLASSES_ROOT\CLSID 登錄機碼，則您可以使用[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)函式來直接建立應用程式的執行個體。<br /><br /> Visual Studio shell 會使用此 CLSID 來執行物件表格 (ROT) 中註冊應用程式自動化物件，使用 ACTIVEOBJECT_WEAK 旗標。 這可讓您使用[GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)函式來擷取應用程式的執行個體的指標。 此外，如果您定義應用程式自動化物件的 ProgID，則 Visual Studio shell 也會註冊應用程式的每個執行個體 ROT 中使用的項目表單 moniker 的*progID*:*processID*，其中*progID*是應用程式的 automation 物件的 ProgID 和*processID*是應用程式執行個體的處理序識別碼。 例如，如果您建立 moniker，如下所示︰<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> 其中`instanceString`是*progID*:*processID*字串。 然後您可以使用`instanceMoniker`與 ROT GetObject 函式，取得執行個體。<br /><br /> 如果省略 ThisVersionDTECLSID 設定，則應用程式是不會公開透過元件物件模型 (COM)。 在此情況下，無法建立應用程式的執行個體呼叫[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)函式，並不能在 ROT 中註冊。<br /><br /> 每個版本的 VSPackage 必須有不同的 CLSID。<br /><br /> 預設值是 Visual Studio automation 物件的應用程式所產生的 GUID。|  
|ThisVersionSolutionCLSID|字串|應用程式的方案物件的 CLSID。<br /><br /> 解決方案自動化物件包含目前開啟的方案中的應用程式和實作的執行個體的相關資訊<xref:EnvDTE._Solution?displayProperty=fullName>介面。</xref:EnvDTE._Solution?displayProperty=fullName><br /><br /> 如果方案 automation 物件正確登錄 HKEY_CLASSES_ROOT\CLSID 登錄機碼，則您可以使用[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)函式來直接建立應用程式的方案物件。<br /><br /> Visual Studio shell 會使用此 CLSID ROT 中註冊的方案 automation 物件，使用 ACTIVEOBJECT_WEAK 旗標。<br /><br /> 如果省略此設定，則方案類別未註冊的元件物件模型 (COM)，而且無法藉由呼叫建立方案物件[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)函式，並不能在 ROT 中註冊。<br /><br /> 預設值是 Visual Studio 方案物件的應用程式所產生的 GUID。|  
|UserFilesSubFolderName|字串|使用者檔案和子資料夾，建立應用程式使用者的我的文件 資料夾底下的子資料夾名稱。<br /><br /> 預設值是應用程式方案檔的名稱。|  
|UserOptsFileExt|字串|應用程式方案使用者選項檔延伸模組。<br /><br /> 預設值是應用程式方案檔的名稱。|  
  
## <a name="binding-path-settings"></a>繫結路徑設定  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] 機碼包含的殼層會檢查組件的目錄清單。 這些目錄會加入至殼層應用程式的私用組件探查的目錄清單。  
  
 根據預設，沒有繫結路徑項目會加入至.pkgdef 檔。 不過，下列 Visual Studio 安裝目錄的子目錄會自動新增至登錄中的 [應用程式繫結路徑] 清單中。  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 若要將目錄新增至繫結路徑，將新增的項目表單的 「*directoryName*"=""，其中*directoryName*是絕對路徑。 例如：  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>設定檔設定  
 下表說明針對每個相關聯的封裝，在 [$RootKey$ \Profile] 下所定義的值。  
  
|名稱|類型|值|  
|----------|----------|-----------|  
|AutoSaveFile|字串|應用程式會儲存自動儲存檔案的目錄。<br /><br /> 預設值是 「 $RootFolder$\Profiles\CurrentSettings.vssettings 」。|  
  
## <a name="package-satellite-dll-settings"></a>封裝附屬 DLL 設定  
 下表描述在下定義的值 [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] 附屬 DLL 的每個相關聯的套件，其中*vsPackageGuid*是相關聯的封裝 GUID。  
  
|名稱|類型|值|  
|----------|----------|-----------|  
|DllName|字串|DLL 的檔案名稱。<br /><br /> 預設值是"*solutionName*ui.dll 」，其中*solutionName*是應用程式方案檔的名稱。|  
|路徑|字串|包含附屬 DLL 的目錄。<br /><br /> 預設值是"$PackageFolder$"。|  
  
## <a name="package-menu-item-settings"></a>封裝功能表項目設定  
 [$RootKey$ \Menus] 登錄機碼會定義應用程式的 UI 資源檔。  
  
 功能表項目值有格式"{*vsUiPackageGuid*}"=" *resourceId*， *versionNumber*」，其中*vsUiPackageGuid*是應用程式 UI 的套件，GUID *resourceId*是包含 UI 項目 CTMENU 資源的資源識別碼和*versionNumber*是 CTMENU 資源的虛擬版本號碼。 如需詳細資訊，請參閱[登錄的 Interop 組件命令處理常式](../extensibility/internals/registering-interop-assembly-command-handlers.md)。  
  
 根據預設，功能表項目的項目會建立應用程式 UI 封裝的.pkgdef 檔中。  
  
 每一個封裝可讓功能表項目，並會隨應用程式的一部分，加入封裝的功能表項目的項目。  
  
## <a name="see-also"></a>另請參閱  
 [自訂獨立的 Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)
