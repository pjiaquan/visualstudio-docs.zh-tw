---
title: "自訂獨立的 Shell |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>自訂獨立的 Shell
藉由變更不同層面的 Visual Studio 使用者介面以及限制的命令與特殊應用程式包含的功能，您可以自訂 Visual Studio 隔離 shell 應用程式。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 Application.pkgdef 檔案  
 獨立的 shell 範本方案包括*SolutionName*。Application.pkgdef 檔案，可讓您修改下列功能︰  
  
##### <a name="the-application-title"></a>應用程式標題  
 您可以自訂應用程式的標題，也就是名稱:"AppName"資料列中的值變更為應用程式的標題列中顯示*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果您不想要顯示目前已載入專案的應用程式標題，變更 「 ShowHierarchyRootInTitle 」 資料列中的值*SolutionName*。Application.pkgdef 檔從 dword:&00000;001 dword:00000000。  
  
##### <a name="the-application-icon"></a>應用程式圖示  
 您可以自訂應用程式圖示，也就是由應用程式名稱應用程式標題列中顯示的圖示。 複製的圖示目錄一樣的圖示。 在**方案總管 中**，將圖示新增至資源檔的資料夾。 然後開啟 VSShellStub.rc 檔案並使用新圖示的名稱來取代 IDI_STUBPROGRAM 的值。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令列標誌  
 您可以自訂的命令列的標誌，是從命令列中，啟動應用程式中的 「 CommandLineLogo 」 資料列的值變更時，會出現的文字*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>使用者名稱的檔案子資料夾  
 您可以變更您的應用程式中的 「 UserFilesSubFolderName 」 資料列的值變更維護使用者檔案的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>在 [新增專案] 對話方塊中的方案樹狀節點的標題  
 您可以自訂方案節點，在 [新增專案] 對話方塊的標題中的 「 NewProjDlgSlnTreeNodeTitle 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>已安裝的範本中的標頭新增專案 對話方塊  
 您可以變更已安裝的範本中的標頭新增專案 對話方塊中的 「 NewProjDlgInstalledTemplatesHdr 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>決定是否要預設隱藏其他檔案  
 您可以指定是否要隱藏其他檔案中的 「 HideMiscellaneousFilesByDefault 」 資料列的值變更預設*SolutionName*。Application.pkgdef 檔案。 若要隱藏其他檔案，將值設定`dword:00000001`，並顯示的檔案，將值`dword:00000000`。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>指出是否要停用 [輸出] 視窗  
 您可以指定是否要停用應用程式中的 [輸出] 視窗中的 「 DisableOutputWindow 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要停用 [輸出] 視窗，請將值`dword:00000001`，若要顯示 [輸出] 視窗，將值設定`dword:00000000`。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>決定是否允許在主視窗已卸除的檔案  
 您可以指定是否要允許應用程式中的主視窗上的已卸除的檔案中的 「 AllowsDroppedFilesOnMainWindow 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要允許卸除的檔案，將值設定`dword:00000001`，不允許卸除的檔案，將值設定`dword:00000000`。  
  
##### <a name="the-default-search-page"></a>預設搜尋網頁  
 您可以自訂網頁瀏覽器上，開啟網頁瀏覽器視窗時，「 DefaultSearchPage 」 資料列中的值變更時所顯示的頁面*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-home-page"></a>預設的首頁  
 您可以自訂 [首頁] 頁面中的 「 DefaultHomePage 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>指出是否隱藏解決方案概念  
 您可以指定是否要隱藏在您的應用程式中的方案中的 「 HideSolutionConcept 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要隱藏方案，請將值`dword:00000001`，並顯示方案，請將值`dword:00000000`。  
  
##### <a name="the-default-debug-engine"></a>預設偵錯引擎  
 您可以變更應用程式中的 「 DefaultDebugEngine 」 資料列的值變更所使用的偵錯引擎*SolutionName*。Application.pkgdef 檔案之 guid 的偵錯引擎。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>使用者選項檔的副檔名  
 您可以變更您的應用程式中的 「 UserOptsFileExt 」 資料列的值變更維護使用者檔案的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-extension"></a>方案檔案的副檔名  
 您可以變更用於您的方案檔案中的 「 SolutionFileExt 」 資料列的值變更的延伸模組*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-user-files-folder-root"></a>預設使用者檔案資料夾根目錄  
 您可以變更使用者檔案的根資料夾的名稱為您的應用程式中的 「 UserFilesSubFolderName 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-creator-identifier"></a>方案檔案建立者識別碼  
 您可以變更您的方案檔案中的 「 SolutionFileCreatorIdentifier 」 資料列的值變更所使用的識別碼*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-projects-location"></a>預設專案位置  
 您可以變更預設專案位置的名稱中的 「 DefaultProjectsLocation 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-application-localization-package"></a>應用程式當地語系化封裝  
 您可以變更用於您的應用程式中的 「 AppLocalizationPackage 」 資料列的值變更當地語系化套件*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>指出是否要在標題中顯示階層的根  
 您可以指定是否要在您的應用程式的標題列中顯示階層的根，「 ShowHierarchyRootInTitle 」 資料列中的值變更*SolutionName*。Application.pkgdef 檔案。 若要顯示階層根目錄，請將值`dword:00000001`，若要隱藏階層的根，將值設定`dword:00000000`。  
  
##### <a name="specifying-a-start-page"></a>指定的起始頁  
 若要指定自訂的應用程式的起始頁中*SolutionName*。Application.pkgdef 檔案設定為 「 DisableStartPage 」 值`dword:00000000`，然後在`[$RootKey$\StartPage\Default]`.xaml 檔案的位置設定的 URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 檔案中*SolutionName*UI 專案，標記為註解 「 No_ShellPkg_startPageCommand 」 項目︰  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 您必須加入.xaml 檔案，以及您需要為任何圖形檔*SolutionName*專案。 這些檔案必須實際將複製到*SolutionName*專案目錄中，不會加入從其他的目錄。  
  
 在所有的檔案，設定**項目類型**屬性**隔離 Shell 檔案**順序檔案的檔案複製到*$RootFolder$*目錄。 (若要設定**項目類型**屬性，以滑鼠右鍵按一下檔案，然後選取**屬性**。 這個屬性可以在底下找到**組態屬性**，**一般**。)  
  
 如需自訂起始頁的詳細資訊，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用獨立 shell 的其他項目  
 您可以使用其他檔案和包含在獨立的 shell 方案範本中，若要進一步自訂您的應用程式的專案。  
  
##### <a name="enabledisable-visual-studio-packages"></a>啟用/停用 Visual Studio 套件  
 *SolutionName*.pkgundef 檔可讓您排除特定封裝，以停用特定類型的 Visual Studio 功能。 例如，下列程式碼︰  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 從專案範本顯示在集合中移除其他檔案專案**新的專案** 對話方塊。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>啟用/停用功能表命令  
 *SolutionName*UI.vsct 檔案包括所有的功能表命令可以獨立 shell 標記為註解清單。 若要停用指定的命令，請取消註解的對應資料列。 例如，若要停用分割視窗/註解，請取消註解`<Define name="No_SplitCommand"/>`資料列。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>用於啟動顯示畫面的點陣圖  
 您可以自訂在啟動顯示畫面，也就是啟動應用程式時，「 SplashScreenBitmap 」 資料列中的值變更時所顯示的視窗上使用的點陣圖*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>說明/關於視窗  
 獨立的 shell 範本中沒有個別的專案，您可以使用自訂 [說明/關於您的應用程式] 對話方塊。 如需詳細資訊，請參閱[逐步解說︰ 建立基本的隔離 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。
