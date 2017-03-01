---
title: "使用並提供服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
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
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>使用並提供服務
服務是兩個 VSPackages 之間的合約。 一個 VSPackage 提供一組特定的介面來使用另一個 VSPackage。 例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務任何 VSPackage 它載入。</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 此服務會提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，這可以用來寫入活動記錄檔。</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 如需詳細資訊，請參閱[How to︰ 使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
 VSPackages 還可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>介面...</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>提供自己的服務  
  
 Visual Studio 提供重要的服務，如下所示︰  
  
|IDE 服務|描述|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供 IDE 存取服務的基本功能、 VSPackages，與登錄的處理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的視窗化與 UI 相關的功能，在 IDE 中，例如建立工具和文件視窗的功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本的方案相關功能，例如列舉專案、 建立新的專案及監視專案的變更的能力。|  
  
## <a name="in-this-section"></a>本章節內容  
 [服務的基本資訊](../extensibility/internals/service-essentials.md)  
 提供 Visual Studio 服務的重要項目。  
  
 [如何︰ 取得服務](../extensibility/how-to-get-a-service.md)  
 討論如何要求 （使用） 服務。  
  
 [如何︰ 提供的服務](../extensibility/how-to-provide-a-service.md)  
 討論如何提供服務。  
  
 [如何︰ 提供非同步的 Visual Studio 服務](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 討論如何提供非同步的服務。  
  
 [How to︰ 服務進行疑難排解](../extensibility/how-to-troubleshoot-services.md)  
 討論常見的問題，並呈現給他們的解決方案。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
