---
title: "實作語法標色 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
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
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>實作語法標色
當語言服務提供語法顏色標示時，剖析器會將一行文字轉換成色彩項目的陣列，並傳回語彙基元的型別對應至這些色彩的項目。 剖析器應該會傳回屬於可設定色彩的項目清單的語彙基元型別。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根據色彩標示器物件指派給適當的權杖型別屬性的程式碼視窗中顯示每個色彩的項目。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]未指定的剖析器介面，以及剖析器實作是完全由您決定。 不過，在 Visual Studio 語言套件專案提供預設剖析器實作。 Managed 程式碼，受管理的封裝架構 (MPF) 提供完整支援色彩標示的文字。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語法著色的新方法的詳細資訊，請參閱[逐步解說︰ 反白顯示文字](../../extensibility/walkthrough-highlighting-text.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>後面接著以色彩標示文字編輯器中的步驟  
  
1.  編輯器 中取得色彩標示器藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  編輯器呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>方法，以判斷色彩標示器是否需要以色彩標示器外部維護每個線路的狀態。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  如果色彩標示器需要外部色彩標示器維護狀態，編輯器便會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法來取得第一個線路的狀態。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  編輯器會針對緩衝區中的每一行，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，執行下列步驟︰</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  一行文字會傳遞至掃描器的文字轉換成語彙基元。 每個語彙基元指定語彙基元的文字和語彙基元的型別。  
  
    2.  語彙基元的型別會轉換成色彩的項目清單中的索引。  
  
    3.  語彙基元資訊用來填滿陣列，陣列的每個項目對應至的行中的字元。 儲存在陣列中的值是可設定色彩的項目清單中的索引。  
  
    4.  每一行都會傳回行結尾處的狀態。  
  
5.  如果色彩標示器需要維持狀態，編輯器會快取該線路的狀態。  
  
6.  編輯器 中呈現的文字時，使用傳回的資訊列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 此時，您需要進行下列步驟：  
  
    1.  每個字元一行中，取得色彩項目的索引。  
  
    2.  如果使用預設色彩的項目，存取編輯器 的色彩的項目清單。  
  
    3.  否則，呼叫語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，以取得色彩的項目。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  使用色彩的項目中的資訊來呈現文字顯示畫面。  
  
## <a name="managed-package-framework-colorizer"></a>受管理的封裝架構色彩標示器  
 受管理的封裝架構 (MPF) 提供實作色彩標示器所需的所有類別。 您的語言服務類別應該繼承<xref:Microsoft.VisualStudio.Package.LanguageService>類別並實作需要的方法。</xref:Microsoft.VisualStudio.Package.LanguageService> 您必須提供掃描器和剖析器藉由實作<xref:Microsoft.VisualStudio.Package.IScanner>介面，並傳回從該介面的執行個體<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法 (必須在實作的方法的其中一個<xref:Microsoft.VisualStudio.Package.LanguageService>類別)。</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> 如需詳細資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)   
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
