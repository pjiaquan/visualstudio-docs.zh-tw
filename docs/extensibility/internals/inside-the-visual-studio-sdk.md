---
title: "在 Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "藍圖，Visual Studio 整合 SDK"
  - "Visual Studio 整合 SDK 藍圖"
  - "整合藍圖，Visual Studio SDK"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# 在 Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本節提供有關 Visual Studio 擴充功能，包括 Visual Studio 架構、 元件、 服務、 結構描述、 公用程式，以及類似的深入資訊。  
  
## 擴充性架構  
 下圖顯示 Visual Studio 擴充性結構。 VSPackages 提供應用程式功能，為服務在 IDE 之間共用。 標準的 IDE 也提供各式各樣的服務，例如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, ，它能提供 IDE 視窗化功能的存取權。  
  
 ![環境架構圖形](../../extensibility/internals/media/environment.png "environment")  
Visual Studio 架構一般化的檢視  
  
## Vspackage  
 VSPackages 是構成和擴充 Visual Studio UI 項目、 服務、 專案、 編輯和設計工具的軟體模組。 VSPackages 是 Visual Studio 的中央架構單位。 如需詳細資訊，請參閱[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## Visual Studio Shell  
 Visual Studio shell 提供基本功能，並支援其元件 VSPackages 與 MEF 擴充功能之間的互通。 如需詳細資訊，請參閱[Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。  
  
## 使用者經驗指導方針  
 如果您計劃適用於 Visual Studio 設計新功能，您應該看看這些指導方針來設計和可用性的秘訣: [Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## 命令  
 命令是完成工作，例如列印文件、 重新整理檢視，或建立新檔案的功能。  
  
 當您擴充 Visual Studio 時，您可以建立命令，並以 Visual Studio shell 進行註冊。 您可以指定這些命令上出現的方式在 IDE 中，例如，功能表或工具列。 自訂命令通常會出現在 **工具** 功能表，然後顯示工具視窗的命令就會出現在 **其他視窗** 子功能表中的 **檢視** 功能表。  
  
 當您建立的命令時，您也必須為它建立事件處理常式。 事件處理常式會判斷命令可看見或是已啟用，讓您可以修改它的文字，以及保證命令啟動時會適當地回應。 在大部分情況下，IDE 會處理命令使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 在 Visual Studio 中的命令會開始根據本機的選取範圍，並繼續最外層的內容，而全域範圍的最內層的命令內容來處理。 新增至主功能表命令會立即可供指令碼。  
  
 如需詳細資訊，請參閱[命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## 功能表和工具列  
 功能表和工具列會提供方法讓使用者叫用命令。 功能表是資料列或資料行的命令，通常會顯示成個別文字工具視窗最上方的項目。 子功能表是當使用者按一下命令，包括一個小箭號時，出現的第二個功能表。 當使用者以滑鼠右鍵按一下特定 UI 項目，則會出現內容功能表。 部分常見的功能表名稱不 **檔案**, ，**編輯**, ，**檢視**, ，和 **視窗**。 如需詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 工具列是資料列或資料行的按鈕和其他控制項，例如下拉式方塊、 清單方塊和文字方塊。 工具列按鈕通常會有圖示的影像的資料夾圖示 **開啟檔案** 命令或印表機的 **列印** 命令。 所有的工具列項目與相關聯的命令。 當您按一下工具列按鈕時，會執行其相關聯的命令。 在下拉式清單控制項時，下拉式清單中的每個項目是不同的命令相關聯的。 某些工具列控制項，例如分隔器控制項是混合。 一方的控制項是工具列按鈕，另一端是顯示數個命令，按一下向下箭號。  
  
## 工具視窗  
 工具視窗在 IDE 中用於顯示資訊。**工具箱**, ，**方案總管\] 中**, ，**屬性** \] 視窗中，和 **網頁瀏覽器** 是工具視窗的範例。  
  
 工具視窗通常會提供各種使用者可以互動的控制項。 比方說， **屬性** 視窗可讓使用者設定的特定用途的物件屬性。**屬性** 視窗是特殊的意義上來說，但也廣泛，因為可用於許多不同的情況。 同樣地， **輸出** 視窗特製化，因為它提供文字為基礎的輸出，但一般，因為在 Visual Studio 中的許多子系統可以用它來提供輸出給 Visual Studio 使用者。  
  
 請考慮下圖的 Visual Studio，其中包含數個工具視窗。  
  
 ![螢幕擷取畫面](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 某些工具視窗會一起停駐的單一窗格會顯示 \[方案總管\] 工具視窗會隱藏其他工具視窗，但可讓它們透過按一下索引標籤。 圖中會顯示兩個其他工具視窗， **錯誤清單** 和 **輸出** \] 視窗中，一起停駐的單一窗格。  
  
 另外也顯示會顯示數個編輯器視窗的主要文件\] 窗格。 雖然工具視窗通常會有一個執行個體 \(例如，您可以開啟只有一個 **方案總管\] 中**\)，編輯器視窗可以有多個執行個體，其中每一個用來編輯個別的文件，但全部都停駐在同一個窗格。 圖中顯示文件\] 窗格具有兩個編輯器視窗、 一個表單設計工具視窗和一個瀏覽器視窗，顯示 \[啟動\] 頁面。 文件\] 窗格中的所有視窗都都可以透過按一下索引標籤上，但包含 EditorPane.cs 檔案 \[編輯器\] 視窗會顯示和使用。  
  
 當您擴充 Visual Studio 時，您可以建立的工具視窗，可以讓 Visual Studio 使用者互動，以擴充。 您也可以建立您自己的編輯器，可讓 Visual Studio 使用者編輯文件。 由於編輯器和工具視窗會整合到 Visual Studio 中，您不必撰寫這些固定或正確顯示在索引標籤。 當它們已正確註冊 Visual Studio 中時，它們會自動在 Visual Studio 中的文件視窗和工具視窗的功能。 如需詳細資訊，請參閱[擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)。  
  
## 文件視窗  
 文件視窗是多重文件介面 \(MDI\) 視窗的框架處理的子視窗。 文件視窗通常會用來裝載在文字編輯器、 表單編輯器 \(也就是設計工具\) 或編輯控制項，但它們也可以裝載其他功能的類型。**新檔案** 對話方塊包含 Visual Studio 提供的文件視窗的範例。  
  
 大部分的編輯器特有的程式設計語言或檔案類型，例如 HTML 網頁、 框架、 c \+ \+ 檔案或標頭檔。 藉由選取的範本中 **新檔案** 對話方塊中，使用者會動態建立文件視窗的編輯器與範本相關聯的檔案類型。 當使用者開啟現有的檔案，也會建立文件視窗。  
  
 文件視窗都會限定在 MDI 工作區。 每個文件視窗具有的最上方的索引標籤，並且定位順序連結到其他可能是 MDI 區域中開啟的視窗。 文件視窗的索引標籤上按一下滑鼠右鍵，就會顯示快顯功能表，其中包含要在 MDI 區分成多個水平或垂直索引標籤群組的選項。 分割 MDI 區域可讓同時檢視多個檔案。 如需詳細資訊，請參閱[文件視窗](../../extensibility/internals/document-windows.md)。  
  
## 編輯器  
 在 Visual Studio 編輯器可讓您自訂並使用您自己的內容類型的 Managed Extensibility Framework \(MEF\) 使用。 在許多情況下您不需要建立 VSPackage 擴充編輯器，不過如果您想要包含的殼層 \(例如，功能表命令或快速鍵\) 的功能，您可以結合 MEF 擴充功能的 VSPackage。  
  
 您也可以建立自訂編輯器，例如，如果您想要讀取和寫入至資料庫，或如果您想要使用設計工具。 您也可以使用外部的編輯器，例如 \[記事本\] 或 Microsoft WordPad。 如需詳細資訊，請參閱[編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)。  
  
## 語言服務  
 如果您想在 Visual Studio 編輯器，以支援新的程式設計關鍵字或甚至是新的程式設計語言，您會建立語言服務。 每個語言服務可能會實作特定編輯器功能完整、 部分，或完全沒有。 依據其設定方式，語言服務可以提供語法反白顯示、 括號對稱、 IntelliSense 支援和編輯器中的其他功能。  
  
 語言服務的核心是剖析器和掃描器。 掃描器 \(或 lexer\) 會將原始程式檔分成稱為 「 語彙基元的項目和剖析器會建立這些語彙基元之間的關聯性。 當您建立語言服務時，您必須實作剖析器和掃描器，如此語彙基元和語言的文法，才能了解 Visual Studio。 您可以建立 managed 或 unmanaged 語言服務。 如需詳細資訊，請參閱[舊版的語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)。  
  
## 專案  
 在 Visual Studio 中，專案會是開發人員用來組織及建置原始碼和其他資源的容器。 專案可讓您組織、 建置、 偵錯及部署程式碼，請參考 Web 服務和資料庫，而且其他資源。 VSPackages 可以擴充 Visual Studio 專案系統提供的專案類型、 專案的子類型，以及自訂工具。  
  
 專案也可能會收集成方案，也就是一群共同建立應用程式的一個或多個專案。 屬於方案的專案和狀態資訊會儲存在兩個方案檔案、 文字為基礎的方案 \(.sln\) 檔和二進位方案使用者選項 \(.suo\) 檔案。 這些檔案是類似於舊版中所使用的群組 \(.vbg\) 檔案 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], ，和工作區 \(.dsw\) 和使用者選項 \(.opt\) 檔案中的舊版本所使用的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]。  
  
 如需詳細資訊，請參閱 [專案](../../extensibility/internals/projects.md) 與 [方案](../../extensibility/internals/solutions.md)。  
  
## 專案和項目範本  
 Visual Studio 包含預先定義的專案範本和專案項目範本。 您可以也讓您自己的範本或取得來自社群的範本，然後將它們整合到 Visual Studio。[MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) 是範本和擴充功能的地方。  
  
 範本包含的專案結構和基本建置特定種類的應用程式、 控制項、 程式庫或類別所需的檔案。 當您想要開發軟體類似的其中一個範本時，建立範本為基礎的專案，然後修改該專案中的檔案。  
  
> [!NOTE]
>  不支援此範本架構 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 專案。 如需有關如何建立資訊 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 專案範本，請參閱 [設計精靈](/visual-cpp/ide/designing-a-wizard)。  
  
 如需詳細資訊，請參閱[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## 內容與選項  
 **屬性** 視窗會顯示單一或多個選取的項目屬性: [擴充屬性](../../extensibility/internals/extending-properties.md) 選項頁面包含一組選項，這些選項屬於特定元件，例如的程式設計語言或 VSPackage: [選項和選項頁面](../../extensibility/internals/options-and-options-pages.md)。 設定是通常與 UI 相關的功能，可以匯入和匯出: [使用者設定的支援](../../extensibility/internals/support-for-user-settings.md)。  
  
## Visual Studio 服務  
 在服務提供一組特定的元件使用的介面。 Visual Studio 會提供一組可供任何元件，包括擴充功能的服務。 例如，Visual Studio 服務可讓工具視窗，顯示或隱藏起來，以動態方式啟用存取說明、 狀態列或使用者介面事件。 在 Visual Studio 編輯器也提供可匯入的編輯器延伸模組的服務。 如需詳細資訊，請參閱[使用並提供服務](../../extensibility/using-and-providing-services.md)。  
  
## 偵錯工具  
 偵錯工具是特定語言偵錯元件的使用者介面。 如果您已建立新的語言服務，您必須建立連結至偵錯工具的特定偵錯引擎。 如需詳細資訊，請參閱[Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## 原始檔控制  
 執行原始檔控制外掛程式或 VSPackage 的相關資訊，請參閱 [原始檔控制](../../extensibility/internals/source-control.md)。  
  
## 精靈  
 您可以使用新的專案類型搭配建立精靈，在建立該類型的新專案時，您的使用者，以便協助精靈做出正確的決策。 如需詳細資訊，請參閱[精靈](../../extensibility/internals/wizards.md)。  
  
## 自訂工具  
 自訂工具可讓您在專案中的項目相關聯的工具，並執行該工具，每次您儲存檔案。 如需詳細資訊，請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## VSSDK 公用程式  
 VSSDK 包含一組公用程式，您可能需要為了要處理的不同層面的 Vspackage。 如需詳細資訊，請參閱[VSSDK 公用程式](../../extensibility/internals/vssdk-utilities.md)。  
  
## 使用 Windows Installer  
 在某些情況下，您可能需要使用 Windows 安裝程式，而不是 VSIX 安裝程式: 例如，您可能需要寫入登錄。 您的擴充功能搭配使用 Windows Installer 的詳細資訊，請參閱 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
## 說明檢視器  
 您可以整合您自己的說明和 F1 頁面說明檢視器。 如需詳細資訊，請參閱[Microsoft 說明檢視器 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。