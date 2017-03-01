---
title: "什麼是 Visual Studio 2015 SDK 的新功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>什麼是 Visual Studio 2015 SDK 的新功能
Visual Studio SDK Visual Studio 2015、 Visual Studio 2015 更新，以及 Visual Studio 2017 具有下列全新和更新功能。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK 更新 1  
 Update 1 包含工具，可協助您有效搭配色彩佈景主題和 Visual Studio 映像服務的擴充功能。  
  
 這些主題位於[VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md)區段︰  
  
-   [色彩佈景主題工具](../extensibility/internals/color-theming-tools.md)協助您建立和編輯 Visual Studio 自訂色彩。  
  
-   [映像服務工具](../extensibility/internals/image-service-tools.md)可讓您使用 Visual Studio 映像的資訊清單檔案。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>將 Visual Studio SDK 加入至 Visual Studio 的新方式  
 啟動 Visual Studio 2015 中，您不需要另外下載 Visual Studio SDK。 相反地，您可以將它安裝為標準安裝程序的一部分或更新版本上安裝時，您可以選擇。 當您開啟或建立 VSIX 方案時，Visual Studio 會要求您安裝 Visual Studio 擴充性工具。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="new-ways-of-creating-extensions"></a>建立擴充功能的新方法  
 您啟動 Visual Studio 2015 SDK 中，有不同的選項，可建立擴充功能，您使用的程式設計語言而定。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic  
 C# 和 Visual Basic 中，會有一套完備的專案項目範本可讓您建立 VSPackages、 功能表命令、 工具視窗、 編輯器的分類器、 編輯器裝飾和編輯器邊界延伸模組。 您可以新增任何或所有這些元件，以標準的 VSIX 專案。 如需詳細資訊，請參閱:  
  
-   [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage 精靈不會再建立擴充功能以 C# 或 Visual Basic。  
  
### <a name="c"></a>C++  
 C + +，VSPackage 精靈支援功能表命令、 工具視窗和自訂編輯器。 尋找在**新的專案** 對話方塊中的**Visual c + + / 擴充性**。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>透過 NuGet VS SDK 參考組件  
 提升可攜性和擴充性專案共用，您可以使用 VS SDK 參考組件的 NuGet 版本。  這些是用於[nuget.org](http://www.nuget.org)發行的[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)可輕鬆地加入至專案或透過 Visual Studio 方案和**參考 / 管理 NuGet 封裝** 對話方塊。 您可以個別將參考加入至特定的擴充性的組件，或新增 VS SDK 參考組件一次使用 VS SDK[中繼封裝](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。 若要深入了解 NuGet，請參閱[NuGet 概觀](http://docs.nuget.org/)和[使用對話方塊管理 NuGet 套件](http://docs.nuget.org/Consume/Package-Manager-Dialog)。  
  
 當您使用 VS SDK 參考組件的 NuGet 版本時，另一位使用者不需要安裝 VS SDK，開啟和建置您的專案。  NuGet 參考組件和 VS SDK 建置工具會自動將該專案在電腦上安裝。  
  
 VS SDK 項目範本用於其參考的 NuGet，並建置工具，讓您取得的 NuGet 優點，根據預設。  
  
> [!NOTE]
>  您可以繼續使用您的專案中安裝 VS SDK 參考組件 (位於\<Visual Studio 安裝位置 > \ VSSDK\VisualStudioIntegration\Common\Assemblies) 並不需要現有的擴充性專案升級為使用 NuGet 封裝。  專案**參考] / [加入參考**對話方塊就會繼續使用安裝 VS SDK 參考組件。  
>   
>  如果您想要修改現有的專案使用 NuGet，請參閱[How to︰ 將 VSPackages 移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)具有擴充性專案更新至 NuGet 封裝區段。  
  
## <a name="light-bulbs"></a>燈泡  
 Roslyn 專案已經提供一個延伸模組程式碼撰寫最令人興奮的新方法。 如需詳細資訊，請參閱[Roslyn](https://github.com/dotnet/Roslyn)。  
  
 燈泡是 VSSDK 所隨附的新功能。 也就是使用 Visual Studio 編輯器中展開以顯示一組程式碼重構動作或內建的程式碼分析器所識別的問題的修正程式的圖示。 如需詳細資訊，請參閱[逐步解說︰ 顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
## <a name="updated-user-experience-guidelines"></a>更新的使用者經驗指導方針  
 Visual Studio 的設計新的擴充功能？ 簽出的更新和擴充[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您可以找到[色彩語彙基元](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)，[字型大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)，[對話方塊版面配置規格](../extensibility/ux-guidelines/layout-for-visual-studio.md)，和其他您需要與 Visual Studio 中完美整合新 UI 的指引。
