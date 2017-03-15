---
title: "語言服務及編輯器延伸模組入門 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>語言服務及編輯器延伸模組入門
若要將語言服務功能，例如大綱、 括號對稱、 IntelliSense 和燈泡，加入您自己的程式語言或任何內容型別，您可以使用編輯器延伸模組。 您也可以自訂的外觀和行為的 Visual Studio 編輯器，例如文字著色、 邊界、 裝飾和其他視覺化項目。 您也可以定義的內容，您的型別，並指定的外觀和行為的文字檢視您的內容會出現。  
  
 若要開始撰寫編輯器延伸模組，使用 Visual Studio sdk 一起安裝的編輯器專案範本。 Visual Studio SDK 是可下載的工具，可讓您輕鬆地使用 VSPackages，或使用 Managed Extensibility Framework (MEF) 開發 Visual Studio 擴充功能，一組。  
  
> [!NOTE]
>  如需 Visual Studio SDK 的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
 我們建議您先了解下列概念和技術撰寫您自己的編輯器延伸模組之前。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 和編輯器延伸模組  
 Visual Studio 編輯器使用者介面 (UI) 是使用 Windows Presentation Foundation (WPF) 來實作。 WPF 提供豐富的視覺效果和一致的程式設計模型的視覺效果的程式碼分開的商務邏輯。 當您建立編輯器延伸模組時，您可以使用許多 WPF 項目和功能。 如需詳細資訊，請參閱[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed 的 Extensibility Framework (MEF) 和編輯器延伸模組  
 在 Visual Studio 編輯器會使用 Managed Extensibility Framework (MEF) 來管理元件與延伸模組。 MEF 也可讓開發人員輕鬆地建立主應用程式，像是 Visual Studio 的擴充功能。 在此架構中，定義延伸模組，根據 MEF 合約，並將它匯出為 MEF 元件組件。 主應用程式管理元件部分，找到這些物件、 註冊，並確定它們會套用至正確的內容。  
  
> [!NOTE]
>  如需在編輯器中的 MEF 的詳細資訊，請參閱[在編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 編輯器擴充點和擴充功能  
 編輯器擴充點的 MEF 元件組件，您可以自訂及擴充。 在某些情況下您可以擴充的擴充點所實作介面，並將它匯出，加上正確的中繼資料。 在其他情況下，只是宣告擴充功能，並將它匯出為特定型別。  
  
 以下是一些基本的編輯器延伸模組種類︰  
  
-   邊界和捲軸  
  
-   Tags  
  
-   裝飾  
  
-   選項  
  
-   IntelliSense  
  
 如需編輯器的擴充點的詳細資訊，請參閱[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)。  
  
## <a name="deploying-editor-extensions"></a>部署編輯器擴充功能  
 在 Visual Studio 中，您會加入名為 source.extension.vsixmanifest 加入方案中，建置方案時，中繼資料檔案，然後已知的資料夾中的二進位檔案和資訊清單的複本加入至 Visual Studio 部署編輯器延伸模組。 資訊清單檔會定義有關擴充功能 （例如，名稱、 作者、 版本和內容類型） 的基本事項。 如需 VSIX 資訊清單檔案，以及如何部署擴充功能的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 當您在電腦上安裝擴充功能時，包括二進位檔和資訊清單中的子資料夾，也是以 Visual Studio。  
  
> [!WARNING]
>  您不必擔心詳細的資訊清單和部署位置，如果您使用其中一個隨附於 Visual Studio 擴充性範本編輯器。 範本會包含所需登錄及部署擴充功能的所有項目。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>在實驗執行個體中執行擴充功能  
 在部署中的下列實驗性資料夾 （Windows Vista 和 Windows 7） 開發擴充功能時，您可以隔離您的 Visual Studio 版本︰  
  
 *%LOCALAPPDATA%*\VisualStudio\10.0Exp\Extensions\\*公司*\\*ExtensionID*  
  
 其中*%LOCALAPPDATA%*的登入的使用者名稱*公司*擁有延伸模組的公司名稱和*ExtensionID*延伸模組的識別碼。  
  
 當您部署延伸模組的實驗性的位置時，它會在偵錯模式中執行。 Visual Studio 的第二個執行個體已啟動，且名為**Microsoft Visual Studio 實驗執行個體**。  
  
## <a name="managing-extensions"></a>管理延伸模組  
 Visual Studio 擴充功能會列在**擴充功能和更新**(在**工具**功能表)。 如果您要測試延伸模組的實驗執行個體中，它會列在**擴充功能和更新**在實驗性的執行個體，但並未列在開發的執行個體。  
  
 如需詳細資訊，請參閱[尋找以及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)。  
  
## <a name="using-templates-to-create-editor-extensions"></a>使用範本建立編輯器延伸模組  
 您可以使用編輯器範本，建立自訂的分類器、 裝飾和邊界的 MEF 擴充功能。 有 C# 和 Visual Basic 專案範本。 如需詳細資訊，請參閱[編輯器項目範本以建立副檔名為](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
 您也可以使用 VSIX 專案範本建立擴充功能。 此範本提供部署任何一種擴充功能，並包含 source.extension.vsixmanifest 檔案、 必要的組件參考和專案檔，其中包含讓您將部署延伸模組，建置工作所需的項目。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
 您也可以建立編輯器 MEF 元件從 Visual Studio 套件擴充功能。 下列逐步解說，如需詳細資訊，請參閱︰  
  
-   [逐步解說︰ 使用 Shell 命令的編輯器延伸模組](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [逐步解說︰ 使用快速鍵的編輯器延伸模組](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
