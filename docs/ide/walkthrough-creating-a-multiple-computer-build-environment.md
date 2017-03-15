---
title: "逐步解說：建立多電腦建置環境 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建置環境, MSBuild"
  - "MSBuild, 在多部電腦上建置"
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 逐步解說：建立多電腦建置環境
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在您的組織內的主機電腦上以安裝Visual Studio 建立組建環境，然後複製各種檔案和設定到其他台電腦，以參與建置。  您不需要在其他電腦上安裝 Visual Studio。  
  
 文件不授予重新分配軟體的權限或提供組建環境給第三方。  
  
||  
|-|  
|免責聲明<br /><br /> 文件在一個基礎現狀提供。  當我們測試中所列步驟時，我們無法徹底地測試每個組態。  我們會嘗試保留文件目前與學習的其他資訊。  本文件之資訊和觀點，包括URL和其他網際網路的網站參考，日後修改之後不另行通知。  Microsoft 不對這裡所提供的資訊做擔保，表示或暗示。  您要負使用它的風險。<br /><br /> 本文件不提供任何對於Microsoft 產品任何智慧財產的合法權限。  您可以以私人或參考為用途複製並使用此文件。<br /><br /> 您沒有義務給Microsoft 任何與文件相關的建議、註解或其他意見。  不過，任何您自願提供的意見可能會用於Microsoft 產品和相關的規格文件或是其他文件，可能會提供為第三方發展自己的成品的依據。  因此，您對於這份文件的任何版本給予 Microsoft 回應或 應用在 Microsoft Offering，即表示您同意: \(a\) Microsoft 可以自由使用，重現，授權，散發，並且將在所有的意見商業化；\(b\) 您可以免費成為第三方，只有必要的這些專利使用使其他產品使用或正在使用將您的意見 Microsoft 產品的所有特定部分； \(c\) 您並不會提供任何 Microsoft 意見 \(i\) 您有根據認定為受所有專利、著作權、任何協力廠商限制其他智慧財產的方法宣告或權限；或者 \(ii\) 受搜尋要求要求所有 Microsoft 提供合併或衍生自這個回應的授權合約，或是其他 Microsoft 智慧財產限制，則會允許對或使用任何協力廠商共用。|  
  
 使用 Team Foundation Build 和在命令列執行 MSBuild，會逐步針對下列作業系統解說。  
  
-   Windows 8 \(x86 和 x64\)  
  
-   Windows 7 旗艦版  
  
-   Windows Server 2008 R2 Standard  
  
 在您完成本逐步解說後面的步驟中，您可以使用多部電腦環境建立這類應用程式:  
  
-   使用 Windows 8 SDK 的 C\+\+ 桌面應用程式  
  
-   以 .NET Framework 4.5 的 Visual Basic 或 C\# 桌面應用程式  
  
 多部電腦環境無法用於建置這類應用程式:  
  
-   [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用程式。  若要建置 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，您必須在組建電腦上安裝 Visual Studio。  
  
-   以 .NET Framework 4 或之前的桌面應用程式。  若要建立這類應用程式，您必須安裝 Visual Studio 或 .NET 參考組件和工具 \(從 Windows 7.1 SDK\) 在組建電腦上。  
  
 本逐步解說分為下列部分:  
  
-   [在電腦上安裝軟體。](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [從主機電腦複製檔案至組建電腦](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [建立登錄設定](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [在組建電腦上設定環境變數](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [將MSBuild組件安裝在組建電腦的全域組件快取 (GAC) 中。](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [建置專案](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [建立建置環境，以便可以簽入至原始檔控制](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## 必要條件  
  
-   Visual Studio Ultimate、Visual Studio Premium 或 Visual Studio Professional 授權的複本。  
  
-   .NET Framework 4.5.1 的複本，您可以從這個網站 [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software) 下載。  
  
##  <a name="InstallingSoftware"></a> 在電腦上安裝軟體。  
 首先，請設定主機電腦然後設定組建電腦。  
  
 您可以安裝在主機電腦上執行 Visual Studio，您可以建立檔案並設定您之後將複製到組建電腦。  您可以安裝在 x86 或 x64 電腦上安裝 Visual Studio，不過，組建電腦的結構必須符合主機電腦的結構。  
  
#### 在電腦上安裝軟體。  
  
1.  在主機電腦上，安裝 Visual Studio。  
  
2.  在組建電腦上，安裝 .NET Framework 4.5。要驗證其安裝，請確定值的登錄機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET Framework 設定了\\ NDP \\ v4 \\ Full@Version 開頭為「4.5 "。  
  
##  <a name="CopyingFiles"></a> 從主機電腦複製檔案至組建電腦  
 本節包含從主機電腦重複特定檔案、編譯器、工具、建立 MSBuild 屬性和登錄設定至組建電腦。  這些指示假設您在主機電腦上的預設位置安裝 Visual Studio；如果您在其他位置，請調整步驟。  
  
-   在 x86 電腦上，預設位置為 C:\\Program Files\\Microsoft Visual Studio 11.0 \\  
  
-   在 x64 電腦上，預設位置為 C:\\Program Files\(x86\)\\Microsoft Visual Studio 11.0 \\  
  
 請注意程式檔案資料夾名稱取決於安裝的作業系統。  在 x86 電腦上，名稱為\\ Program Files \\;在 x64 電腦上，名稱為\\ Program Files \(x86\) \\。  不考慮系統架構，本逐步解說會將程式檔案資料夾為 %ProgramFiles%。  
  
> [!NOTE]
>  在組建電腦上，所有相關的檔案必須位於同一個磁碟；不過，該磁碟機的磁碟機代號與 Visual Studio 在主機電腦上安裝的驅動的磁碟機代號可以不同。  在任何情況下，也就是說，當您在文件中，建立登錄項目 \(如稍後所述\) 必須說明檔案的位置。  
  
#### 複製 Windows SDK 檔案到組建電腦  
  
1.  如果您使用 Windows 8 的 Windows SDK 從主機電腦以遞迴方式安裝，請將這些資料夾加入至組建電腦:  
  
    -   %ProgramFiles% \\ Windows 套件\\ 8.0 \\ bin \\  
  
    -   %ProgramFiles% \\ Windows 套件\\ 8.0 \\目錄\\  
  
    -   %ProgramFiles% \\ Windows \\ 8.0 \\套件 DesignTime \\  
  
    -   %ProgramFiles% \\ Windows 套件\\ 8.0 \\ Include \\  
  
    -   %ProgramFiles% \\ Windows 套件\\ 8.0 \\Lib \\  
  
    -   %ProgramFiles% \\ Windows 套件\\ 8.0 \\ Redist \\  
  
    -   %ProgramFiles% \\ Windows \\ 8.0 \\套件參考\\  
  
     如果您也有這些其他 Windows 8 套件…  
  
    -   Microsoft Windows 評估和部署套件  
  
    -   Microsoft Windows 驅動程式套件  
  
    -   Windows 架構硬體認證套件  
  
     …它們可能已將檔案安裝到上一個步驟清單的 %ProgramFiles% \\ Windows 套件\\ 8.0 \\資料夾，然後，其授權條款可能不允許這些檔案的組建伺服器。  檢查授權條款每個安裝 Windows 套件驗證檔案是否可以複製到組建電腦。  如果授權合約不允許組建伺服器的權限，則請從組建電腦移除檔案。  
  
2.  從主機電腦遞迴地複製下列資料夾加入至組建電腦:  
  
    -   %ProgramFiles% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ bin \\ NETFX 4.0 Tools \\  
  
    -   %ProgramFiles% \\ Common Files \\ Merge Modules \\  
  
    -   \\%Program Files%\\Microsoft Visual Studio 11.0\\VC\\。  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ Tools \\ProjectComponents\\  
  
    -   \\%Program Files%\\MSBuild\\Microsoft.Cpp\\v4.0\\V110\\  
  
    -   \\%Program Files%\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5\\  
  
    -   \\%Program Files%\\Reference Assemblies\\Microsoft\\Framework\\.NETFramework\\v4.5\\  
  
3.  從主機電腦複製檔案至組建電腦  
  
    -   \\%Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msobj110.dll  
  
    -   \\%Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   \\%Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbcore.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbsrv.exe  
  
    -   \\%Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msvcdis110.dll  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ Tools \\makehm.exe  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ Tools \\ VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ Tools\\ vsvars32.bat  
  
4.  下列 Visual C\+\+ 執行階段程需要文件庫，才能在組建的組建輸出電腦。例如，為自動化測試的一部分。  檔案通常位於 %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ VC \\ redist \\ x86 或\\ %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ VC \\ redist \\ x64 \\資料夾下的子資料夾，根據系統架構。  在 x86 系統，複製 x86 二進位到\\ Windows \\ System32 \\資料夾。  在 x64 系統，複製 x86 二進位到 Windows \\ SysWOW64 \\資料夾和 x64 二進位到 Windows \\ System32 \\資料夾。  
  
    -   Microsoft.VC110.ATL \\ \\ atl110.dll  
  
    -   Microsoft.VC110.CRT \\ msvcp110.dll  
  
    -   Microsoft.VC110.CRT \\ msvcr110.dll  
  
    -   Microsoft.VC110.CXXAMP \\ \\ vcamp110.dll  
  
    -   Microsoft.VC110.MFC \\ \\ mfc110.dll  
  
    -   Microsoft.VC110.MFC \\mfc110u.dll  
  
    -   Microsoft.VC110.MFC \\ mfcm110.dll  
  
    -   Microsoft.VC110.MFC \\mfcm110u.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110chs.dll  
  
    -   Microsoft.VC110.MFCLOC\\mfc110cht.dll  
  
    -   Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110enu.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110esn.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110fra.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110ita.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110jpn.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110kor.dll  
  
    -   Microsoft.VC110.MFCLOC \\mfc110rus.dll  
  
    -   Microsoft.VC110.OPENMP \\ vcomp110.dll  
  
5.  從\\Debug\_NonRedist \\ x86\\ 或 \\ Debug\_NonRedist \\ x64\\資料夾中複製 下列檔案到組建電腦，如 [準備測試電腦以執行偵錯可執行檔](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)中所述。  其他檔案可能不會複製。  
  
    -   Microsoft.VC110.DebugCRT \\ msvcp110d.dll  
  
    -   Microsoft.VC110.DebugCRT \\msvcr110d.dll  
  
    -   Microsoft.VC110.DebugCXXAMP \\ vcamp110d.dll  
  
    -   Microsoft.VC110.DebugMFC \\ mfc110d.dll  
  
    -   Microsoft.VC110.DebugMFC \\mfc110ud.dll  
  
    -   Microsoft.VC110.DebugMFC \\ mfcm110d.dll  
  
    -   Microsoft.VC110.DebugMFC \\mfcm110ud.dll  
  
    -   Microsoft.VC110.DebugOpenMP \\ vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> 建立登錄設定  
 您必須建立登錄項目設定 MSBuild 的設定。  
  
#### 若要建立登錄設定  
  
1.  識別登錄項目的上層資料夾。  所有登錄項目建立相同父系機碼下。  在 x86 電腦上，父系機碼是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.  在 x64 電腦上，父系機碼是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.  不考慮系統架構，本逐步解說會將父系機碼為 %RegistryRoot%。  
  
    > [!NOTE]
    >  如果您的主機電腦結構與該組建電腦不同，請務必使用在每台電腦上適當的父系機碼。  如果自動化匯出處理序，這特別重要。  
    >   
    >  此外，如果您所使用的組建電腦上由不同的磁碟機代號在主機電腦上使用，請確定變更登錄項目值使其相符。  
  
2.  若要在組建電腦上執行下列登錄項目。  這些輸入是字串型別 \(在登錄中的\=\= REG\_SZ」型別\)。  設定這些輸入的值與比較的輸入相同的值在主機電腦上執行。  
  
    -   %RegistryRoot% \\ .NETFramework \\ v4.0.30319 \\ AssemblyFoldersEx \\ VCMSBuild 公用 Assemblies@ \(預設值\)  
  
    -   %RegistryRoot% \\ Microsoft SDKs \\ Windows \\ v8.0@InstallationFolder  
  
    -   %RegistryRoot% \\ Microsoft SDKs \\ Windows \\ v8.0A@InstallationFolder  
  
    -   %RegistryRoot% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ WinSDK\-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ WinSDK\-NetFx40Tools\-x86@InstallationFolder  
  
    -   %RegistryRoot% \\ VisualStudio \\ 11.0@Source 目錄  
  
    -   %RegistryRoot% \\ VisualStudio \\ 11.0 \\設定了\\ VC@ProductDir  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\ VC7@FrameworkDir32  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\ VC7@FrameworkDir64  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\ VC7@FrameworkVer32  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\ VC7@FrameworkVer64  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\ VC7@11.0  
  
    -   %RegistryRoot% \\ VisualStudio \\ SxS \\VS7@11.0  
  
    -   %RegistryRoot% \\ Windows \\套件安裝的 Roots@KitsRoot  
  
    -   %RegistryRoot% \\ MSBuild \\ ToolsVersions \\ 4.0 \\ 11.0@VCTargetsPath  
  
    -   %RegistryRoot% \\ MSBuild \\ ToolsVersions \\ 4.0 \\ 11.0@VCTargetsPath10  
  
    -   %RegistryRoot% \\ MSBuild \\ ToolsVersions \\ 4.0 \\ 11.0@VCTargetsPath11  
  
     在 x64 組建電腦上，也請建立下列登錄項目並參閱主機電腦判斷如何設定它。  
  
    -   %RegistryRoot% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ WinSDK\-NetFx40Tools\-x64@InstallationFolder  
  
     如果您的組建電腦 x64，而且想要使用 MSBuild 64 位元版本，或者，如果您使用在 x64 電腦上安裝 Team Foundation Server 組建服務，您必須在原生 64 位元登錄的下列登錄項目。  請參閱主機電腦判斷如何設定這些項目。  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Setup\\VS@ProductDir  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> 在組建電腦上設定環境變數  
 若要在組建電腦上的 MSBuild，您必須設定 PATH 環境變數。  您可以使用 vcvarsall.bat 設定變數，也可以手動設定它們。  
  
#### 使用 vcvarsall.bat 設定環境變數  
  
-   開啟在組建電腦上 %Program Files% \\ Microsoft Visual Studio 11.0 \\ VC \\ vcvarsall.bat 的命令提示字元視窗。  您可以使用命令列引數會指定您要使用 x86 的工具組，原生 x64 或 x64 跨平台編譯器。  如果您不指定命令列引數，就會使用 x86 工具組。  
  
     下表中描述 vcvarsall.bat 支援的引數。  
  
    |Vcvarsall.bat 引數|編譯器|組建電腦架構|組建輸出架構|  
    |----------------------|---------|------------|------------|  
    |x86\(預設\)|32 位元原生|x86, x64|x86|  
    |x86\_amd64|x64 Cross|x86, x64|x64|  
    |amd64|x64 機器|x64|x64|  
  
     如果 vcvarsall.bat 執行成功，沒有錯誤訊息會顯示您可以略過下一個步驟並繼續進行本文件的 [將MSBuild組件安裝在組建電腦的全域組件快取 (GAC) 中。](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) 一節。  
  
#### 手動設定的環境變數。  
  
1.  手動設定命令列環境，請加入這個路徑加入至 PATH 環境變數:  
  
    -   %Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\。  
  
2.  或者，您也可以將下列路徑路徑變數更容易使用 MSBuild 建置方案。  
  
     如果您要使用原生 32 位元 MSBuild，請將這些路徑路徑變數:  
  
    -   %Program Files% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ bin \\ NETFX 4.0 Tools \\  
  
    -   %windir%\\Microsoft.NET\\Framework\\v4.0.30319\\  
  
     如果您要使用原生 64 位元 MSBuild，請將這些路徑路徑變數:  
  
    -   %Program Files% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ bin \\ NETFX 4.0 Tools \\x64  
  
    -   %windir%\\Microsoft.NET\\Framework64\\v4.0.30319\\  
  
##  <a name="InstallingMSBuildToGAC"></a> 將MSBuild組件安裝在組建電腦的全域組件快取 \(GAC\) 中。  
 MSBuild 需要一些額外的組件安裝到組建電腦的 GAC 中。  
  
#### 複製組件從主機電腦並將它們安裝在組建電腦  
  
1.  從主機電腦組件複製下列資料夾至組建電腦:  因為它們會安裝至 GAC，無論您在組建電腦上的地方放置它們都沒有關係。  
  
    -   %ProgramFiles% \\ MSBuild \\ Microsoft.Cpp \\ v4.0 \\ v110 \\ Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ IDE \\ CommonExtensions \\ Microsoft \\ VC \\ Projects \\ Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ IDE \\ PublicAssemblies \\ Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  若要將組件安裝到 GAC，找出 gacutil.exe 組建電腦時，它在 %ProgramFiles% \\ Microsoft SDKs \\ Windows \\ v8.0A \\ bin \\ NETFX 4.0 Tools \\。  如果找不到這個資料夾，請重複此逐步解說中的 [從主機電腦複製檔案至組建電腦](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) 一節的步驟。  
  
     開啟具有系統管理權限的命令提示字元視窗並執行每個檔案的這個命令:  
  
     **gacutil \-i \<file\>**  
  
    > [!NOTE]
    >  重新啟動可能對組件所需的完整安裝到 GAC。  
  
##  <a name="BuildingProjects"></a> 建置專案  
 您可以使用 Team Foundation Build 建立 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 專案和方案，或建立在命令列。  當您使用 Team Foundation Build 建置專案時，會叫用對應於系統架構的 MSBuild 可執行檔。在命令列中，您可以使用 MSBuild 32 位元或 64 位元 MSBuild，因此，您可以選取 MSBuild 結構將 PATH 環境變數或直接叫用結構特定 MSBuild 可執行檔。  
  
 若要使用 msbuild.exe 在命令提示字元中，執行下列命令，其中 *solution.sln* 是您的方案名稱的預留位置。  
  
 **msbuild** *solution.sln*  
  
 如需如何在命令列使用MSBuild，請參閱[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  若要建立 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 專案，您必須使用「v110」平台工具組。  如果您不要編輯 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 專案檔，您可以使用這個命令列引數，您可以設定平台工具組:  
>   
>  **msbuild** *solution.sln* **\/p:PlatformToolset\=v110**  
  
##  <a name="CreatingForSourceControl"></a> 建立建置環境，以便可以簽入至原始檔控制  
 您可以建立可在不同的電腦上部署，而且不需要 GAC'ing 檔案或修改登錄設定的建置環境。  下列步驟可讓您完成這項工作。  調整這些步驟建置環境的唯一特性。  
  
> [!NOTE]
>  您必須停用累加建置在建置期間，以便 tracker.exe 不會擲回錯誤。  若要停用累加建置，請將此組建參數:  
>   
>  **msbuild** *solution.sln* **\/p:TrackFileAccess\=false**  
  
#### 建立可以簽入至原始檔控制的建置環境  
  
1.  在處機電腦上建立一個「倉庫」的目錄。  
  
     這些步驟將目錄做為 %Depot%。  
  
2.  除了在您建立的 %Depot% 目錄下貼上複製目錄和檔案 \(如本逐步解說的 [從主機電腦複製檔案至組建電腦](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) 一節所述\)。  例如，請複製 %ProgramFiles% \\ Windows 套件\\ 8.0 \\ bin \\至%Depot% 套件\\ Windows \\ 8.0 \\ bin \\。  
  
3.  當檔案在 %Depot% 時貼上，請進行這些變更:  
  
    -   在 %Depot% \\ MSBuild \\ Microsoft.Cpp \\ v4.0 \\ v110 \\ Microsoft.CPP.Targets，\\ Microsoft.Cpp.InvalidPlatforms.targets \\，\\ Microsoft.cppbuild.targets\\，和\\ Microsoft.CppCommon.targets \\，變更每個執行個體  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110， Version\= 4.0.0.0， Culture\=neutral， PublicKeyToken\=b03f5f7f11d50a3a」  
  
         設為  
  
         AssemblyFile\= " $ \(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll」。  
  
         目前命名依賴的組件 GAC'ed。  
  
    -   在 %Depot% \\ MSBuild \\ Microsoft.Cpp \\ v4.0 \\ v110 \\ Microsoft.CPPClean.Targets，變更每個執行個體  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110， Version\= 4.0.0.0， Culture\=neutral， PublicKeyToken\=b03f5f7f11d50a3a」  
  
         設為  
  
         AssemblyFile\= " $ \(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll」。  
  
4.  建立 .props 檔 \(例如， Partner.AutoImports.props 並將它包含在您的專案資料夾的根目錄。  這個檔案是用來設定 MSBuild 來尋找各種資源的變數。  如果變數不是由這個檔案設定，它們會依賴登錄值的其他 .props 檔與 .targets 檔案設定。  由於我們不設定任何登錄值，這些變數是空的，則建置將會失敗。  相反地，請將這個加入 Partner.AutoImports.props:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  在每個專案檔中，將下行程式碼頂端，，在 `<Project Default Targets…>` 這一行之後。  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  變更命令列環境如下:  
  
    -   設定 Depot\=*location of the Depot directory that you created in step 1*  
  
    -   集合 path\=%path%;*location of MSBuild on the computer*; %Depot% \\ Windows \\ System32; %Depot% \\ Windows \\ SysWOW64; %Depot% \\ Microsoft Visual Studio 11.0 \\ Common7 \\ IDE \\  
  
         原生 64 位元建置的，對 64 位元 MSBuild 的點。  
  
## 請參閱  
 [準備測試電腦以執行偵錯可執行檔](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)