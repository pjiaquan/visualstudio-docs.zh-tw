---
title: "逐步解說: 建立基本的獨立的 Shell 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell，逐步解說"
  - "Shell [Visual Studio]，逐步解說"
  - "逐步解說 [Visual Studio]，隔離 shell 架構應用程式"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# 逐步解說: 建立基本的獨立的 Shell 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說示範如何建立獨立的 shell 方案、 自訂 \[說明\] 工具視窗，以及建立安裝程式來安裝獨立的 shell。  
  
## 必要條件  
 若要依照本逐步解說，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 若要部署獨立的 shell，您也必須使用 Visual Studio Shell \(獨立模式\) 可轉散發套件。  
  
## 建立獨立的 Shell 方案  
 本節說明如何使用 Visual Studio Shell 外掛式主控專案範本建立獨立的 shell 的方案。 解決方案包含下列專案:  
  
-   *SolutionName*。AboutBoxPackage 專案，可讓您自訂 \[說明\/關於\] 對話方塊的外觀。  
  
-   ShellExtensionsVSIX 專案，其中包含定義獨立的 shell 應用程式的不同元件的 source.extension.vsixmanifest 檔案。  
  
-   *SolutionName* 產生叫用獨立的 shell 應用程式的可執行檔的專案。 此專案包含自訂殼層資料夾，可讓您以 customiz 外觀和行為的獨立的 shell 應用程式。  
  
-   *SolutionName* UI 專案，會產生附屬組件會定義使用中的功能表命令和可當地語系化的字串。  
  
#### 若要建立基本的獨立的 shell 方案  
  
1.  開啟 Visual Studio 並建立新的專案。  
  
2.  在 **新的專案** \] 視窗中，展開 **其他專案類型** 然後 **擴充性**。 選取 **Visual Studio Shell 外掛式主控** 專案範本。  
  
3.  將專案命名為 `MyVSShellStub` 和指定的位置。 請確定 **為方案建立目錄** 已核取，然後按一下 \[ **確定**。  
  
     新的方案會出現在 **方案總管\] 中**。  
  
4.  建置方案並開始偵錯獨立的 shell 應用程式。  
  
     Visual Studio 隔離 shell 隨即出現。 標題列讀取 **MyVSShellStub**。 標題列圖示是從 \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico 產生。  
  
## 自訂應用程式名稱和圖示  
 您可以在標題列中使用的名稱以及貴公司的標誌標示您的應用程式。 下列步驟示範如何變更所變更的套件定義檔 MyVSShellStub.Application.pkgdef 自訂應用程式標題列中顯示圖示和名稱。  
  
#### 若要自訂的應用程式名稱和圖示  
  
1.  在 MyVSShellStub 專案中，開啟 \\Shell Customization\\MyVSShellStub.Application.pkgdef。  
  
2.  變更 `AppName` 項目值 **:"AppName"\="Fabrikam 音樂 Editor"**  
  
3.  若要變更應用程式圖示，將不同的圖示複製到 \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\ 目錄。 將現有的 ApplicationIcon.ico 檔案重新命名為 ApplicationIcon1.ico。 將新的檔案重新命名為 ApplicationIcon.ico。  
  
4.  建置方案並開始偵錯。 獨立的 shell IDE 隨即出現。 標題列有您新的圖示，字組旁邊 **Fabrikam 音樂編輯器**。  
  
## 自訂預設網頁瀏覽器首頁  
 本節說明如何變更預設的首頁的 **網頁瀏覽器** \] 視窗中的變更封裝定義檔。  
  
#### 若要自訂預設網頁瀏覽器首頁  
  
1.  在 MyVSShellStub.Application.pkgdef 檔案中，變更 `DefaultHomePage` "http:\/\/www.microsoft.com"的項目值。  
  
2.  重建 MyVSShellStub 專案。  
  
3.  建置方案並開始偵錯。  
  
4.  在 **檢視 \/ 其他視窗**, ，按一下 \[ **網頁瀏覽器**。**網頁瀏覽器** \] 視窗會顯示 Microsoft Corporation 首頁。  
  
## 移除列印命令  
 在獨立的 shell UI 專案.vsct 檔組成一組宣告的形式 `<Define name=No_`*元素*`>`, ，其中 *項目* 是其中一個標準的 Visual Studio 功能表和命令。  
  
 如果宣告是取消註解，該功能表或命令會從獨立 shell 排除。 相反地，如果宣告標記為註解，則功能表或命令包含在獨立 shell。  
  
 在下列步驟中，您取消註解列印命令.vsct 檔案中。  
  
#### 若要移除的列印命令  
  
1.  確認 **列印** 命令會出現在 **檔案** 獨立的 shell 應用程式中的功能表。  
  
2.  在 MyVSShellStubUI 專案中，開啟 \\Resource Files\\MyVSShellStubUI.vsct 進行編輯。  
  
3.  這一行取消註解:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  這會移除列印命令。  
  
5.  開始偵錯獨立的 shell 應用程式。 確認 **檔案 \/ 列印** 命令已不存在。  
  
## 從獨立 Shell 中移除功能  
 您可以移除一些編輯.pkgundef 檔案，如果您不想這些功能在隔離的自訂殼層應用程式中使用 Visual Studio 會載入的封裝。 您在其中 $RootKey$ \\Packages 的登錄機碼的子機碼中指定的套件。  
  
> [!NOTE]
>  若要尋找的 Visual Studio Guid 功能，請參閱 [Visual Studio 功能的封裝 Guid](../extensibility/package-guids-of-visual-studio-features.md)。  
  
 下列程序顯示如何移除 XML 編輯器與獨立的 shell。  
  
#### 若要移除 XML 編輯器  
  
1.  開啟 MyVSShellStub.pkgundef 檔案 MyVSShellStub 專案的 Shell 自訂資料夾中。  
  
2.  取消註解下列這一行:  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  重建方案並開始偵錯獨立的 shell。 開啟 XML 檔案，例如 \\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct。 確認檔案中的 XML 關鍵字未以色彩標示和輸入 「 \< 」 的行上不會使 XML 工具提示。  
  
## 自訂 \[說明\/關於\] 對話方塊  
 您可以自訂 \[說明\/關於\] 方塊中，這會建立為獨立的 shell 專案範本的一部分。  
  
#### 若要自訂公司名稱  
  
1.  公司名稱、 著作權資訊、 產品版本和產品描述中找到 MyVSShellStub.AboutBoxPackage 專案中，\\Properties\\AssemblyInfo.cs 檔案中。 開啟這個檔案。  
  
2.  變更 `AssemblyCompany` 值 **Fabrikam**, 、 `AssemblyProduct` 和 `AssemblyTitle` 值 **Fabrikam 音樂編輯器**, ，而 `AssemblyCopyright` 值 **2015 著作權 © Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  若要新增產品的說明，請變更 `AssemblyDescription` 值 **Fabrikam 音樂編輯器的描述。**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  開始偵錯，並在獨立的 shell 應用程式中，開啟 **說明 \/ 關於** 方塊。 您應該會看到已變更的字串。 說明\/關於\] 對話方塊的標題是相同 `AssemblyTitle` AssemblyInfo.cs 中的值。  
  
5.  內容 **說明\/關於** MyVSShellStub.AboutBoxPackage\\AboutBox.xaml 檔案中找到方塊本身。 若要變更 \[說明\/關於\] 方塊的寬度，請移至 `AboutDialogStyle` 區塊，並設定 `Width` 屬性設為 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  重建方案並開始偵錯獨立的 shell。 說明\/關於\] 對話方塊應該是大約正方形。  
  
## 獨立的 Shell 應用程式的部署之前  
 獨立的 shell 應用程式可以安裝在任何具有 Visual Studio Shell \(獨立模式\) 可轉散發套件的電腦上。 如需可轉散發套件的詳細資訊，請參閱 [Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298) 網站。  
  
## 獨立的 Shell 應用程式部署  
 您藉由建立安裝專案部署到目標電腦應用程式獨立的 shell。 您必須指定這些項目:  
  
-   在目標電腦上的檔案與資料夾配置。  
  
-   啟動條件，以確保.NET Framework 和 Visual Studio shell 執行階段會安裝在目標電腦上。  
  
 下列程序中，您必須在電腦上安裝 InstallShield Limited Edition。  
  
#### 若要建立安裝專案  
  
1.  在 **方案總管\] 中**, ，以滑鼠右鍵按一下方案節點，然後按一下 **加入新的專案**。  
  
2.  在 **新的專案** 對話方塊方塊中，展開 **其他專案類型** ，然後選取 **安裝和部署**。 選取 \[InstallShield 範本。 將新專案 `MySetup` 然後按一下 \[ **確定**。  
  
3.  如果已安裝 InstallShield 限量版，則繼續下一個步驟。  
  
     如果您尚未安裝 InstallShield 限量版，會出現 InstallShield 下載頁面。 依照指示下載並安裝此產品中，選擇 InstallShield 與您的 Visual Studio 版本相容的版本。 您必須決定是否要登錄的 InstallShield 安裝，或使用它來評估。 完成安裝之後，您必須重新啟動 Visual Studio。  
  
    > [!IMPORTANT]
    >  您建立的 InstallShield 專案之前，您必須以系統管理員身分啟動 Visual Studio。 如果不這麼做，您會收到錯誤，建置專案時。  
  
 接下來的步驟示範如何設定安裝專案。  
  
> [!IMPORTANT]
>  請確定您已先設定安裝專案建立獨立的 shell 專案的發行組態至少一次。  
  
#### 若要設定安裝專案  
  
1.  在 **方案總管\] 中**, 下 **MySetup** 專案中，選擇 \[ **專案助理**。 在底部的資料列 **專案助理** \] 視窗中，選擇 \[ **應用程式資訊**。 輸入 **Fabrikam** 為您的公司名稱和 **Fabrikam 音樂編輯器** 做為應用程式名稱。 選擇在右下方的向前箭號 **專案助理**。  
  
2.  選取 **是** 下 **應用程式需要在電腦上安裝任何軟體?** ，然後選取 **Microsoft.NET Framework 4.5 的完整套件**。  
  
3.  選擇 **應用程式檔案** 底部的視窗\] 按鈕，並確定 **Fabrikam 音樂編輯器** 選取資料夾。  
  
4.  選擇 **加入檔案** \] 按鈕。 在 **加入檔案** 對話方塊方塊中，加入下列檔案從 **MyVSShellStub\\Release** 資料夾:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  按一下 \[ **加入專案輸出** 按鈕，然後加入 **MyVSShellStub\/主要輸出**。 按一下 \[**確定**\]。  
  
6.  在左窗格中，在 **目的地電腦**, ，以滑鼠右鍵按一下 **Fabrikam 音樂編輯器 \[INSTALLDIR\]** 節點並新增 **新資料夾** 名為 **延伸模組**。  
  
7.  以滑鼠右鍵按一下 **延伸** 的左窗格中的節點，並新增名為的新資料夾 **應用程式**。  
  
8.  選取 **應用程式** 資料夾，然後按一下 **加入專案輸出** \] 按鈕，然後從 MyVSShellStub.AboutBoxPackage 專案中選取 \[主要輸出。  
  
9. 按一下 \[ **加入檔案** 按鈕，然後從 \\MyVSShellStub\\Release\\Extensions\\Application\\ 資料夾中，加入下列檔案:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 以滑鼠右鍵按一下 **Fabrikam 音樂編輯器 \[INSTALLDIR\]** 的左窗格中的節點，並新增名為的新資料夾 **1033年**。  
  
11. 選取 \[1033年\] 資料夾，然後按一下 **加入專案輸出** 按鈕，然後選取從 MyVSShellStubUI 專案的主要輸出。  
  
12. 移至 **應用程式捷徑** 視窗。  
  
13. 按一下 \[ **新增** 建立捷徑，並選取 **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**。  
  
14. 移至 **安裝會談** 窗格。  
  
15. 若要設定的所有項目 **否**。  
  
16. 在 **方案總管\] 中**, ，MySetup 專案中，開啟 **Define Setup Requirements and 動作 \\ 需求**。**需求** \] 視窗隨即開啟。  
  
17. 以滑鼠右鍵按一下 **系統軟體需求** ，然後選取 **建立新的啟動條件**。**系統搜尋精靈** 隨即出現。  
  
18. 在 **您想要尋找?** \] 窗格中，選擇 \[ **登錄項目** 下拉式清單中按一下 **下一步**。  
  
19. 在 **您想要尋找?** 窗格中，選取 **HKEY\_LOCAL\_MACHINE** 登錄根目錄。 輸入 **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 64 位元系統或 **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 32 位元系統，並輸入 **安裝** 做為登錄值。 按一下 \[下一步\]。  
  
20. 在 **您想要的值?** \] 窗格中，輸入 **此產品所需的 Visual Studio 2015 隔離 Shell 可轉散發套件進行安裝。** 作為顯示文字，然後按一下 **完成**。  
  
21. 重建獨立的 shell 方案建立安裝專案。  
  
     您可以在下列資料夾中找到的 setup.exe 檔案:  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## 測試安裝程式  
 若要測試安裝，請將 setup.exe 檔案複製到另一部電腦並執行安裝程式可執行檔。 您應該能夠執行獨立的 shell 應用程式。