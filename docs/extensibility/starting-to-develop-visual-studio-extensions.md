---
title: "開始開發 Visual Studio 擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取得已啟動，Visual Studio 整合"
  - "Visual Studio 中整合"
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# 開始開發 Visual Studio 擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您撰寫過 Visual Studio 擴充功能之前，您可能會有一些問題。 我們列出一些最常見的。 如果您沒有看到您要尋找的資訊，請使用意見反應按鈕 \(**是此頁面有幫助?** 螢幕的底部\) 詢問您想要。  
  
## 我需要哪些軟體開發 Visual Studio 擴充功能?  
 您需要安裝 Visual Studio 2015 SDK，除了 Visual Studio 2015 開發 Visual Studio 擴充功能。   您可以安裝 Visual Studio 2015 SDK 的一般安裝，或您可以在稍後安裝。 如需有關如何安裝 Visual Studio SDK 的詳細資訊，請參閱 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 與 Visual Studio 擴充功能可以做哪些事情?  
 海闊天空地談到想像不同 Visual Studio 擴充功能。 當然，大部分的擴充功能必須與撰寫程式碼，但不具有這種情況。 以下是一些擴充功能，您可以建置各種類型的範例:  
  
-   不隨附在 Visual Studio 中的語法著色、 IntelliSense 和編譯器和偵錯支援的語言支援  
  
-   擴充核心的產能工具與其他的範本、 程式碼重整、 新對話或工具視窗的 IDE 體驗  
  
-   定義域專屬設計或雲端支援的資料等案例的設計工具  
  
 如需擴充功能的範例，請參閱 [Visual Studio 元件庫](https://visualstudiogallery.msdn.microsoft.com/)。 您也可以看看 [Visual Studio 開啟來源 Extensions](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md)。  
  
## 可以擴充 Visual Studio 功能?  
 理論上，您可以擴充 Visual Studio 的任何一部分: 功能表、 工具列、 命令、 windows、 方案、 專案、 編輯及等等。  
  
 實際上，我們發現大多數人想要擴充的功能是命令、 功能表和工具列、 視窗、 IntelliSense 和專案。 相關章節的連結如下:  
  
-   [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md): 將您自己的項目加入至 Visual Studio 的功能表和工具列。 您可以使用它們來啟動 Visual Studio 功能或您自己的外部協助應用程式。 您也可以提供自訂快速鍵的功能表項目。  
  
-   [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md): 擴充現有的工具視窗，或建立您自己的工具視窗。 比方說，您可以加入新的屬性以 **屬性**, ，或者您可以建立新的工具視窗加入其他功能。  
  
-   [編輯器和語言服務擴充功能](../extensibility/editor-and-language-service-extensions.md): 新增您自己的自訂 Visual Studio 語言提供的 IntelliSense，或建立新的程式設計語言的支援。 您可以建立新的陳述式完成、 建議和新 QuickInfo 工具提示。 燈泡，您可以將重構的建議和程式碼修正，支援新的程式設計語言。  
  
-   [擴充專案](../extensibility/extending-projects.md)  
  
-   [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)  
  
-   [擴充屬性和 \[屬性\] 視窗](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)  
  
-   [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio 隔離 Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> 哪些專案範本所提供的 VSSDK?  
 兩個主要類型的擴充功能是 VSPackages 與 MEF 擴充功能。 一般而言，VSPackage 擴充功能可用的延伸模組，利用或延伸命令、 工具視窗和專案。 MEF 擴充功能用來擴充或自訂 Visual Studio 編輯器中。  
  
 Visual C\# 和 Visual Basic 的延伸模組，VSSDK 會提供與建立功能表命令、 工具視窗和編輯器延伸模組的新項目範本，您可以使用空白 VSIX 專案範本。 如需詳細資訊，請參閱[什麼是 Visual Studio 2015 SDK 的新功能](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。 您也可以使用此範本以封裝專案範本、 程式碼片段和其他成品以散發給其他使用者。  
  
 C \+ \+，VSPackage 精靈中提供的程式碼加入功能表命令、 工具視窗和自訂編輯器。  
  
 獨立 Shell 範本用來封裝的版本，您可以加上商標，並將發佈為您自己的 Visual Studio shell 擴充功能。 下列主題說明如何開始使用每一種副檔名:  
  
-   功能表命令: [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   工具視窗: [建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   編輯器延伸模組: [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本 Vspackage: [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX 專案範本: [開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio 隔離 shell: [逐步解說: 建立基本的獨立的 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## 如何取得看起來像是 Visual Studio 擴充功能?  
 取得設計您的擴充功能中的使用者介面很棒的訣竅 [Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## 哪裡可以找到 VSSDK 程式碼的範例?  
 在上一節中列出的連結中都有提供逐步解說，示範如何實作特定功能。 您也可以尋找開放原始碼 GitHub 上的 VSSDK 範例 [Visual Studio 範例](https://aka.ms/vs2015sdksamples)。  
  
## 我要如何散發 my 擴充性?  
 您可以在另一部電腦上安裝擴充功能，或將它傳送給您的朋友為.vsix 檔案，按兩下您安裝。 您可以深入了解有關在 VSIX 套件 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 您也可以發行您的擴充功能可讓您更大量的 Visual Studio 客戶看到 Visual Studio Gallery 上。 封裝組件庫的擴充功能的範例，請參閱 [逐步解說: 發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 如需有關您要如何發佈於組件庫的詳細資訊，請參閱 [產品和 Visual Studio 擴充功能](https://visualstudiogallery.msdn.microsoft.com/)。