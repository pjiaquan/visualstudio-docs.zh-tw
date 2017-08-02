---
title: "原始檔控制整合概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
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
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節將比較兩種方式整合到 Visual Studio 原始檔控制。原始檔控制外掛程式並提供原始檔控制解決方案，並反白顯示新的原始檔控制功能的 VSPackage。 Visual Studio 可讓您手動切換原始檔控制 VSPackages 及原始檔控制外掛程式，以及自動方案為基礎的切換。  
  
## <a name="source-control-integration"></a>原始檔控制整合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始檔控制整合選項。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，還是整合外掛程式，根據原始檔控制外掛程式 API （先前稱為 MSSCCI API），同時使用 Visual Studio 原始檔控制使用者介面 (UI) 提供基本的原始檔控制功能。 原始檔控制 VSPackage，相反地，提供新的深層整合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適用於需要高層級的複雜度，以及 「 自治 」 在原始檔控制模型中的原始檔控制整合的路徑。  
  
 ![原始檔控制概觀](~/docs/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>原始檔控制外掛程式  
 所有版本的 Visual Studio 都支援原始檔控制外掛程式 API 規格 1.2 版做為整合的路徑。 原始檔控制外掛程式實作器寫入的實作中所述的原始檔控制整合和註冊所需的原始檔控制外掛程式 API 功能[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。 在這種方式，使用整合式開發環境 (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI 對話方塊，例如簽入、 簽出、 工具/選項屬性頁面、 工具列和原始檔控制圖像 （glyph）。 原始檔控制外掛程式 API 嚴格遵循確保輕鬆整合到 Visual Studio 和簡單的使用者體驗。 這表示原始檔控制外掛程式必須實作大部分的函式和詳細的 API 中的回呼。  
  
 若要實作的原始檔控制外掛程式使用原始檔控制外掛程式 API，請遵循下列步驟︰  
  
1.  建立實作中指定的函式的 DLL[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。  
  
2.  藉由適當的登錄項目登錄 DLL (述[How to︰ 安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  建立協助程式 UI 和顯示當系統提示您的原始檔控制配接器套件 （處理透過原始檔控制外掛程式的原始檔控制功能的 Visual Studio 元件）  
  
 在原始檔控制命令的回應，Visual Studio IDE 提供可用的基本作業的標準 UI，然後將資訊傳遞至原始檔控制外掛程式透過原始檔控制外掛程式 API 中定義的函數。 進階選項，請原始檔控制外掛程式可能呼叫來呈現它自己的 UI，例如，瀏覽原始檔控制專案。 這表示，使用者可能會看見兩個可能是不同的樣式的 UI 處理與原始檔控制時︰ Visual Studio 會顯示 UI 和原始檔控制外掛程式呈現的 UI。 這是進階的原始檔控制作業與最為明顯。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>若要實作原始檔控制外掛程式的缺點  
  
-   如需進階的功能，使用者可能會看到兩個不同的樣式的介面，導致混淆。  
  
-   原始檔控制外掛程式會侷限於原始檔控制外掛程式 API 所隱含的原始檔控制模型。  
  
-   原始檔控制外掛程式 API 可能太嚴格，某些原始檔控制案例。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>實作原始檔控制外掛程式的優點  
  
-   Visual Studio 會提供所有基本的原始檔控制作業的 UI，讓原始檔控制外掛程式沒有實作可能很複雜的 UI。  
  
-   嚴格的 API，因為原始檔控制外掛程式可以輕易地與外部來源控制程式互動以提供更豐富的功能;Visual Studio 不負責過許多原始檔控制功能的完成方式，只會根據原始檔控制外掛程式 API 來完成。  
  
-   就很容易實作的原始檔控制外掛程式比原始檔控制 VSPackage。  
  
## <a name="source-control-vspackage"></a>原始檔控制 VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]可讓 Visual Studio 的 Visual Studio 提供的原始檔控制使用者介面完全取代原始檔控制功能的 完全控制與深度整合。 原始檔控制 VSPackage 註冊使用 Visual Studio，並提供原始檔控制功能。 雖然許多原始檔控制 VSPackages 可以向 Visual Studio 中，只有一種可使用一次。 使用中時，原始檔控制 VSPackage 會具有完整控制權的原始檔控制功能和外觀 Visual Studio 中。 所有其他原始檔控制可能在系統中登錄的 VSPackages 非作用中且不會完全顯示任何 UI。  
  
 實作了原始檔控制 VSPackage 需要 「 所有或執行任何動作 」 的策略。 原始檔控制 VSPackage 的建立者必須投入大量的精力在實作幾個來源控制項的介面和新的 UI 項目 （對話方塊、 功能表和工具列） 涵蓋整個來源控制功能。 請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)如需詳細資訊。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>若要實作的原始檔控制 VSPackage 的缺點  
  
-   VSPackage 必須實作一些複雜的介面與 Visual Studio 順利整合。  
  
-   VSPackage 必須提供所有 UI 所需的原始檔控制。Visual Studio 會提供任何協助此區域中。  
  
-   原始檔控制 VSPackage 可感知繫結至 Visual Studio，並讓功能不能輕易與共用原始檔控制程式的外部版本無法使用獨立的程式。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>若要實作的原始檔控制 VSPackage 的優點  
  
-   因為 VSPackage 具有完整控制權的原始檔控制 UI 和功能，使用者會看到原始檔控制的順暢介面。  
  
-   VSPackage 並不僅限於特定原始檔控制模型。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制](../../extensibility/internals/source-control.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [原始檔控制中的新功能](../../extensibility/internals/what-s-new-in-source-control.md)
