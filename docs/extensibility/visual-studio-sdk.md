---
title: "Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: b3cd444e48893057a057c39c515e51ff8b509b34
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK 可協助您擴充 Visual Studio 功能或整合到 Visual Studio 的新功能。 您可以發佈您的擴充功能給其他使用者，以及 Visual Studio 組件庫。 下列是一些可擴充 Visual Studio 的方法：  
  
-   將命令、 按鈕、 功能表和其他 UI 項目新增至 IDE  
  
-   加入新功能的工具視窗  
  
-   指定的語言，來擴充 IntelliSense 或 IntelliSense 提供新的程式設計語言  
  
-   使用提供的提示與建議，協助開發人員撰寫更好的程式碼的燈泡  
  
-   啟用新的語言支援  
  
-   加入自訂的專案類型  
  
-   觸及數百萬開發人員透過 Visual Studio 組件庫  
  
 如果您撰寫過 Visual Studio 擴充功能之前，您應該會發現這些功能以及在詳細資訊[開始開發 Visual Studio 擴充功能](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK  
 Visual Studio SDK 是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>什麼是 Visual Studio 2017 SDK 的新功能  
 Visual Studio SDK 有一些新功能，例如輕量型方案負載和 VSIX v3 格式，以及最新變更，這可能需要更新您的擴充功能的支援。 如需詳細資訊，請參閱[的新功能 Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者經驗指導方針  
 取得設計您的擴充功能中的使用者介面很棒的訣竅[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
 您也可以了解如何讓您看起來漂亮高 DPI 裝置上使用的擴充我們[定址 DPI 問題](../extensibility/addressing-dpi-issues2.md)主題。  
  
 利用[映像服務與類別目錄](../extensibility/image-service-and-catalog.md)絕佳的映像管理和支援高 DPI 與主題。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>尋找及安裝現有的 Visual Studio 擴充功能  
 您可以找到 Visual Studio 擴充功能**擴充功能和更新**上的對話方塊**工具**功能表。 如需詳細資訊，請參閱[尋找以及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)。 您也可以尋找擴充功能中的[Visual Studio 組件庫](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考  
 您可以尋找在 Visual Studio SDK 的 API 參考[Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例  
 您可以在 GitHub 上找到的 VS SDK 延伸模組的開放原始碼範例[Visual Studio 範例](https://aka.ms/vs2015sdksamples)。 此 GitHub 儲存機制包含範例，示範 Visual Studio 中可延伸的各種功能。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源  
 如果您有疑問的 VSSDK，或想要分享開發擴充功能，您可以使用[Visual Studio 擴充性論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS 群組聊天](https://gitter.im/Microsoft/extendvs)。  
  
 您可以找到更多資訊[VSX Arcana 部落格](http://blogs.msdn.com/b/vsx/)和 Microsoft Mvp 所撰寫的部落格的數目︰  
  
-   [最愛的 Visual Studio 擴充功能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [擴充 Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>另請參閱  
 [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [如何︰ 將擴充性專案移轉至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [常見問題集︰ 將增益集轉換成 VSPackage 擴充功能](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [管理多個執行緒在 Managed 程式碼](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [將命令加入至工具列](../extensibility/adding-commands-to-toolbars.md)   
 [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)   
 [編輯器和語言服務擴充功能](../extensibility/editor-and-language-service-extensions.md)   
 [擴充專案](../extensibility/extending-projects.md)   
 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)   
 [建立自訂專案和項目範本](../extensibility/creating-custom-project-and-item-templates.md)   
 [擴充屬性和 [屬性] 視窗](../extensibility/extending-properties-and-the-property-window.md)   
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio 隔離 Shell](../extensibility/visual-studio-isolated-shell.md)   
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)   
 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK 支援](../extensibility/support-for-the-visual-studio-sdk.md)   
 [封存](../extensibility/archive.md)   
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)
