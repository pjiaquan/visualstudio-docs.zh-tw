---
title: "如何︰ 將擴充性專案移轉至 Visual Studio 2017 |Microsoft 文件"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 09f14e5b28a506d4f2112f82ee4fd6b0855a8f93
ms.openlocfilehash: 67e143e1b95a0e4d881d7d6bccae0d7445897aa2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>如何︰ 將擴充性專案移轉至 Visual Studio 2017

>**注意︰**這份文件為初步資訊而且根據 Visual Studio 2017 RC 版本。

本文件說明如何升級至 Visual Studio 2017 擴充性專案。 除了說明如何更新專案檔，並說明如何從延伸模組資訊清單版本 2 (VSIX v2) 升級至新版本 3 VSIX 資訊清單的格式 (VSIX v3)。

## <a name="install-visual-studio-2017-rc-with-required-workloads"></a>安裝 Visual Studio 2017 RC，必要的工作負載

請確定您的安裝包含下列工作負載︰

* .NET 桌面開發
* Visual Studio 擴充功能開發

## <a name="open-vsix-solution-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟 VSIX 方案

所有的 VSIX 專案將需要 Visual Studio 2017 主要版本單向升級。

會更新專案檔 (例如 *.csproj):

* MinimumVisualStudioVersion-現在設定為 15.0
* OldToolsVersion (如果先前存在)-現在設定為 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>更新 Microsoft.VSSDK.BuildTools NuGet 封裝

>**注意︰**如果您的方案不會參考 Microsoft.VSSDK.BuildTools NuGet 封裝，您可以略過此步驟。

若要建置您的擴充功能，在新的 VSIX v3 （第 3 版） 格式，您的方案將需要使用新的 VSSDK 建置工具來建置。 這會安裝 Visual Studio 2017 rc，但您的 VSIX v2 擴充功能可能會保留透過 NuGet 用較舊版本的參考。 如果是的話，您必須手動安裝更新的 Microsoft.VSSDK.BuildTools NuGet 封裝您的解決方案。 此 RC 版本期間，此封裝將會處於 「 預先發行 」 狀態。

若要更新 Microsoft.VSSDK.BuildTools NuGet 的參考︰

* 以滑鼠右鍵按一下方案，然後選擇 **管理方案的 NuGet 封裝...**
* 瀏覽至**更新** 索引標籤。
* 核取方塊以**包含發行前版本**。
* 選取 Microsoft.VSSDK.BuildTools （最新版本）。
* 按下**更新**。

![VSSDK 建置工具](media/vssdk-build-tools.png)

>**注意︰**螢幕擷取畫面顯示 BuildTools 的不同版本。 請選取 RC 版本。

## <a name="make-changes-to-the-vsix-extension-manifest"></a>變更 VSIX 擴充功能資訊清單

若要確保使用者的 Visual Studio 安裝程式已執行此擴充功能所需的所有組件，指定延伸模組資訊清單檔案中的所有必要條件元件或封裝。 當使用者嘗試安裝擴充功能時，VSIXInstaller 會檢查是否會安裝所有必要條件。 若缺少某些，將會提示使用者安裝遺漏的元件擴充功能的安裝程序的一部分。

* 編輯擴充功能資訊清單檔案 （通常稱為 source.extension.vsixmanifest）。
* 請確定`InstallationTarget`包含 15.0。
* （如下列範例所示），請加入必要的安裝必要條件。
  * 我們建議您指定只安裝的必要條件元件識別碼。
  * 請參閱此文件的結尾區段[指示識別元件識別碼](#finding-component-ids)。

範例：

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>選項︰ 使用設計工具來變更 VSIX 擴充功能資訊清單

而不是直接編輯資訊清單的 XML，您可以使用新**必要條件**會為您更新 索引標籤中選取必要條件的資訊清單設計工具和 XML。

>**注意︰**資訊清單設計工具只允許您選取目前的 Visual Studio 執行個體所安裝的元件 （不工作負載或套件）。 如果您需要新增工作負載、 封裝或目前未安裝的元件的必要條件，請直接編輯 XML 資訊清單。

* 開啟 [設計] source.extension.vsixmanifest 檔案。
* 選取**必要條件** 索引標籤，然後按下**新增** 按鈕。

  ![VSIX 資訊清單設計工具](media/vsix-manifest-designer.png)

* **加入新必要條件**視窗隨即開啟。

  ![新增 vsix 必要條件](media/add-vsix-prerequisite.png)

* 按一下下拉式清單中的**名稱**，然後選取所需的必要條件。
* 如有必要，請更新版本。

  >注意: [版本] 欄位會預先填入目前安裝的元件，與範圍橫跨最多 （但不是包括） 版本元件的下一個主要版本。

  ![新增 roslyn 必要條件](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>如果從預覽 4 或 5 預覽移轉

* 取代`SetupDependencies`與`Prerequisites`和移出的項目`Installer`項目。 `Prerequisites`現在位於 直接在`PackageManifest`項目。
* [選用]移除`GenerateVsixV3`項目。 （這是預覽 5 中只有需要。）`GenerateVsixV3`超過 5 預覽版本中會忽略項目。

## <a name="update-debug-settings-for-project"></a>更新專案的偵錯設定

如果您想要偵錯您的 Visual Studio 的實驗執行個體中的擴充功能，請確定專案設定**偵錯** > **起始動作**有**啟動外部程式︰**值設為您的 Visual Studio 2017 安裝的 devenv.exe 檔案。

它可能如下︰

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![啟動外部程式](media/start-external-program.png)

>**注意︰**偵錯起始動作通常會儲存在。 副檔名為.csproj.user 檔案。 這個檔案通常包含在.gitignore 檔案，並因此，不通常會儲存其他專案時使用檔案認可至原始檔控制。 因此，如果您有提取您的方案從原始檔控制的全新很可能專案會有任何值為 起始動作。 使用 Visual Studio 2017 建立新的 VSIX 專案都有。 以指向目前的 Visual Studio 安裝目錄的預設值建立副檔名為.csproj.user 檔案。 不過如果您要移轉的 VSIX v2 延伸模組，則可能的。 副檔名為.csproj.user 檔案將包含參考先前的 Visual Studio 版本的安裝目錄。 設定的值**偵錯** > **起始動作**將允許正確 Visual Studio 實驗性執行個體啟動時您嘗試偵錯您的擴充功能。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>請檢查正確 （如 VSIX v3)，建置擴充功能

* 建立 VSIX 專案。
* 將解壓縮產生的 VSIX。
  * 預設值，VSIX 檔案生活在 bin/Debug 或 bin/Release 為 [YourCustomExtension].vsix。
  * 若要輕鬆地檢視內容的.zip 檔案重新命名.vsix。
* 檢查有三個檔案︰
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>當已安裝所有必要的必要條件檢查

VSIX 成功安裝在電腦安裝所有必要先決條件的測試。

>**注意︰**安裝之前任何延伸模組，請關閉所有 Visual Studio 執行個體。

嘗試安裝擴充功能︰

* 在 Visual Studio 2017 RC

![在 Visual Studio 2017 VSIX 安裝程式](media/vsixinstaller-vs-2017.png)

* 選擇性︰ 檢查先前的 Visual Studio 版本。
  * 證明回溯相容性。
  * 應可適用於 Visual Studio 2012、 Visual Studio 2013、 Visual Studio 2015。
* 選擇性︰ 檢查 VSIX 安裝程式版本檢查，提供選擇的版本。
  * 包含了舊版的 Visual Studio （如果安裝的話）。
  * 包含 Visual Studio 2017 RC。

如果最近開啟 Visual Studio，您可能會看到像這樣的對話方塊︰

![vs 執行處理程序](media/vs-running-processes.png)

等候所有處理序關閉，或以手動方式結束工作。 您可以找到處理程序所列的名稱，或使用括號中列出的 PID。

>**注意︰**這些處理程序將不會自動關閉 Visual Studio 執行個體正在執行時。 請確定您已關閉所有執行個體上 – 包括其他使用者，從 Visual studio，然後繼續重試。

## <a name="check-when-missing-the-required-prerequisites"></a>當遺失所需的必要條件檢查

* 嘗試延伸模組的機器上安裝 Visual Studio 2017 rc 並不會包含在必要條件 （如上所述） 中定義的所有元件。
* 請檢查安裝識別遺漏的元件/s 和列為 VSIXInstaller 中的必要條件。
* 注意︰ 提高權限都必須如果任何必要元件需要安裝擴充功能。

![vsixinstaller 遺漏的必要條件](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>決定元件

相依性時，您會發現一個相依性會對應到多個元件。 若要判斷哪些相依性，您應該指定為您的必要條件，我們建議您選擇的元件，類似於您的擴充功能，並同時考慮您的使用者和元件的何種他們最有可能已安裝或不介意安裝。 我們也建議您所需的必要條件，滿足可讓您擴充功能執行的最小的方式和其他功能的擴充功能有休眠如果某些元件不會偵測到他們的建置。

若要進一步提供指引，我們已找出幾個常見的擴充功能類型和其建議的必要條件︰

擴充功能類型 | 顯示名稱 |    ID
--- | --- | ---
編輯器 | Visual Studio 核心編輯器    | Microsoft.VisualStudio.CoreEditor
Roslyn | C# 和 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 受管理的桌面工作負載的核心 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
偵錯工具 | 在 Just-in-time 偵錯工具 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>尋找元件識別碼

依 Visual Studio 產品的元件清單位於[Visual Studio 2017 工作負載與元件識別碼](https://aka.ms/vs2017componentIDs)。 您在您的資訊清單中的必要條件識別碼中使用這些元件識別碼。

如果您不確定哪一個元件包含特定的二進位檔，下載[-> 二進位對應試算表元件](https://aka.ms/vs2017componentid-binaries)。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel 工作表中有四個資料行︰**元件名稱**， **ComponentId**，**版本**，和**二進位 / 檔案名稱**。  您可以使用篩選來搜尋並尋找特定元件和二進位檔。

針對您所有的參考，必須先決定哪些是核心編輯器 (Microsoft.VisualStudio.Component.CoreEditor) 元件中。  至少，我們所需的核心編輯器元件，以指定為所有擴充功能的必要元件。 參考也會保留不在核心編輯器中，將篩選條件中的加入**二進位碼檔案 / 檔案名稱**一節，以尋找具有任何這些參考子集的元件。

例如：

* 如果您有偵錯工具擴充功能，而且知道您的專案具有 VSDebugEng.dll 和 VSDebug.dll 的參考，按一下 [篩選] 按鈕，在**二進位碼檔案 / 檔案名稱**標頭。  搜尋 「 VSDebugEng.dll 」，並選取 [確定]。  接下來，按一下 [篩選] 按鈕，在**二進位碼檔案 / 檔案名稱**標頭一次，並搜尋 「 VSDebug.dll 」。  選取核取方塊 」 加入目前的選取範圍來篩選 」，然後選取 [確定]。  現在查看**元件名稱**了大部分的元件與延伸模組類型。 在此範例中，您會選擇的時間只需偵錯工具，將它加入至您 vsixmanifest。
* 如果您知道您的專案會處理與偵錯工具項目，您可以搜尋 「 偵錯工具 」 篩選器的 [搜尋] 方塊中查看哪些元件包含偵錯工具在其名稱。
