---
title: "傳送 Visual Studio 擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 部署"
  - "VSIX 部署"
  - "附屬 Dll，在 VSIX 套件"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 傳送 Visual Studio 擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

完成開發您的擴充功能之後，您可以將它安裝在其他電腦上、 分享您的朋友和同事，或發行 Visual Studio Gallery 上。 在這一節我們將說明您只需要以發佈及維護您的擴充功能的所有事情: 使用.vsix 檔案、 發佈、 當地語系化，以及更新。  
  
## 使用 VSIX 擴充功能  
 您可以建立空白的 VSIX 專案，並接著加入不同的項目範本，以建立 VSIX 擴充功能。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
 您可以使用 VSIX 格式來封裝專案範本、 項目範本，VSPackages，Managed Extensibility Framework \(MEF\) 元件， **工具箱** 控制項、 組件和自訂型別 \(這包括自訂的啟動頁面\)。 VSIX 格式會使用以檔案為基礎的部署。 如需 VSIX 套件的詳細資訊，請參閱 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)。  
  
 VSIX 格式不支援安裝的程式碼片段。 它也不支援某些其他功能，例如寫入至全域組件快取 \(GAC\) 或系統登錄。 如果您需要寫入至 GAC 中，或是在安裝中的登錄，您必須使用 Windows Installer。 如需詳細資訊，請參閱[準備 Windows Installer 部署擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。  
  
## 發佈您的擴充功能至 Visual Studio 元件庫  
 您可以擴充散佈給其他人只要郵件方式.vsix 檔案，或放在伺服器上。 但在很多人的手中取得您的程式碼的最佳方式是將它放在 [Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847)。 Visual Studio 組件庫延伸模組都可透過 Visual Studio 使用者 **擴充功能和更新**。 如需詳細資訊，請參閱[尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)。  
  
 如需示範如何將延伸模組上傳至 Visual Studio 組件庫的完整範例，請參閱 [逐步解說: 發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。  
  
## 私用組件庫  
 當您開發控制項、 範本和工具，則您可以張貼到內部網路上的私用組件庫與您的組織共用它們。 如需詳細資訊，請參閱[私用組件庫](../extensibility/private-galleries.md)。  
  
## 當地語系化您的擴充功能  
 如果您計劃發行您的擴充功能在不同的地區設定中，您應該考慮當地語系化。 如需相關說明，請參閱 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## 更新和版本控制您的擴充功能  
 發佈您的擴充功能之後，我們將介紹當您需要更新的時間。 若要了解如何更新已發行 Visual Studio Gallery 的擴充功能，請參閱 [如何︰ 更新擴充功能](../extensibility/how-to-update-a-visual-studio-extension.md)。  
  
 您可以設定您的擴充功能，以支援多個版本的 Visual Studio。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)|說明如何使用 VSIX 專案範本安裝自訂專案範本。|  
|[VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 套件的元件。|  
|[VSIX 專案範本](../extensibility/vsix-project-template.md)|提供有關如何封裝和發行延伸模組的逐步指示。|  
|[當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)|說明如何藉由使用 extension.vsixlangpack 檔案，安裝程序提供當地語系化的文字。|  
|[如何︰ 更新擴充功能](../extensibility/how-to-update-a-visual-studio-extension.md)|說明如何更新您的系統上的擴充，以及如何將更新部署至現有的 Visual Studio 擴充功能。|  
|[如何︰ 將相依性加入至 VSIX 套件](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|描述如何將參考加入至 VSIX 部署套件。|  
|[準備 Windows Installer 部署擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|說明如何將延伸模組使用 Windows Installer 部署。|  
|[簽署 VSIX 封裝](../extensibility/signing-vsix-packages.md)|說明如何簽署 VSIX 封裝。|  
|[私用組件庫](../extensibility/private-galleries.md)|說明如何建立私用組件庫延伸模組。|  
|[支援多個版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|示範如何延伸模組支援多個版本的 Visual Studio。|