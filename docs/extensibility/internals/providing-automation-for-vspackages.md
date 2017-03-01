---
title: "提供自動化的 VSPackages |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
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
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>提供自動化的 Vspackage
有兩種主要的方式，提供您 VSPackages 的自動化︰ 藉由實作 VSPackage 特定物件，並藉由實作標準 automation 物件。 一般而言，這些是一起用來擴充自動化模型的環境。  
  
## <a name="vspackage-specific-objects"></a>VSPackage 特定物件  
 Automation 模型內的特定位置必須要提供特有 VSPackage 的 automation 物件。 比方說，新的專案需要不同只 VSPackage 所提供的物件。 這些物件的名稱輸入登錄中，且透過呼叫環境取得`DTE`物件。  
  
 自動化取用者會使用透過標準物件的物件屬性所提供的物件時，您也可以取得 VSPackage 特定物件。 例如，標準`Window`物件具有`Object`屬性中，通常稱為`Windows.Object`屬性。 當取用者呼叫`Window.Object`在 VSPackage 中實作的視窗，您將傳回您自己設計的特定自動化物件。  
  
#### <a name="projects"></a>專案  
 VSPackages 可擴充新的專案類型，透過其自己的 VSPackage 特定物件的 automation 模型。 從物件提供新的 automation 物件的 VSPackage 區分唯一專案的主要目的<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>或<xref:VSLangProj80.VSProject2>物件。</xref:VSLangProj80.VSProject2> </xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> 此差異很方便，當您想要提供挑出或逐一查看您的其他專案類型，除了專案類型的方法應該出現的並排在方案中。 如需詳細資訊，請參閱[公開專案物件](../../extensibility/internals/exposing-project-objects.md)。  
  
#### <a name="events"></a>事件  
 環境的事件架構提供了另一個位置，以新增您自己的 VSPackage 特定物件。 例如，藉由建立您自己的唯一事件物件，您可以擴充專案的環境的事件模型。 您可能想要提供您自己的事件，當新的項目加入您自己的專案類型。 如需詳細資訊，請參閱[公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。  
  
#### <a name="window-objects"></a>視窗物件  
 Windows 可以傳遞回 VSPackage 特定自動化物件至環境時呼叫。 實作衍生自物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，<xref:EnvDTE.IExtensibleObject>或`IDispatch`，傳遞回到延伸已決定位置所在的視窗物件的屬性。</xref:EnvDTE.IExtensibleObject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> 例如，您可以使用這種方法提供自動化設置在視窗框架的控制項。 此物件及任何其他可能需要延伸的物件的語意都是您設計的。 如需詳細資訊，請參閱[How to︰ 針對 Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。  
  
#### <a name="options-pages-on-the-tools-menu"></a>在 [工具] 功能表上的 [選項] 頁  
 您可以建立頁面，以擴充的工具、 選項 automation 模型，透過實作網頁並將資訊新增至登錄，以建立您自己的選項。 然後可以透過像任何其他選項頁面的環境物件模型呼叫您的網頁。 如果您要加入至透過 VSPackages 環境功能的設計需要 [選項] 頁，您應該加入的自動化支援。 如需詳細資訊，請參閱[選項頁面的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)。  
  
## <a name="standard-automation-objects"></a>標準 Automation 物件  
 若要擴充專案自動化，您也實作標準 automation 物件 (衍生自`IDispatch`)，獨立除外的其他專案物件，並實作標準的方法和屬性。 標準物件的範例包括專案的物件，例如插入方案階層架構`Projects`， `Project`， `ProjectItem`，和`ProjectItems`。 每個新的專案型別應該實作這些物件 （而且可能是其他的語意 （semantics） 根據您的專案）。  
  
 就某方面來說，這些物件可提供特定的 VSPackage 專案物件相反的優點。 所有標準 automation 物件可讓您的專案就像其他任何專案支援相同物件的通用方式使用。 因此，增益集，針對一般撰寫`Project`和`ProjectItem`物件可以根據任何類型的專案運作。 如需詳細資訊，請參閱[專案模型](../../extensibility/internals/project-modeling.md)。
