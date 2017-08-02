---
title: "提供語言服務內容中使用舊版 API |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
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
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>提供語言服務內容中使用舊版 API
有兩個選項，以提供使用者內容中使用的語言服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器︰ 提供文字標記內容，或提供所有的使用者內容。 此處所述每個之間的差異。  
  
 在提供連接到您自己的編輯器語言服務內容的詳細資訊，請參閱[How to︰ 將內容提供編輯器](../extensibility/how-to-provide-context-for-editors.md)。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>編輯器提供文字標記內容  
 若要提供內容的文字標記中所指示的編譯器錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器，請實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 在此案例中，語言服務的資料指標是文字標記上時，才提供內容。 這可讓編輯器提供至游標處關鍵字**動態說明**不含任何屬性 視窗。  
  
## <a name="provide-all-user-context-to-the-editor"></a>提供所有的使用者內容編輯器  
 如果您要建立語言服務，並使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器 中，則您可以實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>介面，以提供語言服務內容。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 實作的`IVsLanguageContextProvider`，編輯器中，負責更新內容包附加的內容封包 （集合）。 當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>介面上的閒置時間，內容包在此內容包查詢更新的編輯器。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 編輯器 中，應該會更新編輯器，並將指標傳遞給內容包，然後通知語言服務。 這是藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>編輯器語言服務的方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> 使用內容包指標，語言服務可以立即加入和移除屬性和關鍵字。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 有兩種不同的方式來實作`IVsLanguageContextProvider`:  
  
-   提供內容包關鍵字  
  
     若要更新的內容包呼叫編輯器時，傳入適當的關鍵字和屬性，然後傳回`S_OK`。 這個傳回值會指示要保留的關鍵字和屬性的內容，而不是提供內容包在游標處關鍵字編輯器。  
  
-   從游標處關鍵字取得關鍵字  
  
     若要更新的內容包呼叫編輯器時，傳遞適當的屬性，然後傳回`E_FAIL`。 這個傳回值會指示要保留您在內容包中的屬性，但更新內容包中的游標處關鍵字編輯器。  
  
 下圖說明如何提供內容的語言服務會實作以`IVsLanguageContextProvider`。  
  
 ![LangServiceImplementation2 圖形](~/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
語言服務內容  
  
 您可以在圖表中，看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文字編輯器已附加至它的內容封包。 此內容包指向三個不同的子內容包︰ 語言服務、 預設編輯器和文字標記。 語言服務及文字標記子內容包包含屬性和關鍵字的語言服務如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>實作介面時，以及文字標記如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面的實作。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 如果您不實作這些介面之一，編輯器會提供內容關鍵字的預設編輯器子內容包游標所在的位置。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>內容的指導方針編輯器和設計工具  
 設計工具和編輯器必須提供的編輯器或設計工具視窗的一般關鍵字。 這麼做是為了讓使用者按下 F1 時，將會顯示的設計工具或編輯器的一般，但適當，說明主題。 編輯器必須，此外，提供目前的游標處關鍵字，或是提供關鍵詞彙，根據目前的選取項目。 這可確保指向或當使用者按下 F1 時，請選取顯示的文字或 UI 項目 [說明] 主題。 設計工具提供在設計工具，例如在表單上的按鈕中的選取項目內容。 編輯器和設計工具也必須連接到語言服務中所述[舊版語言服務 Essentials](../extensibility/internals/legacy-language-service-essentials.md)。
