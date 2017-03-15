---
title: "舊版的語言服務 Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>舊版的語言服務的基本資訊
您必須提供的程式語言整合到 Visual Studio 語言服務。 本主題說明可在舊版的語言服務的功能。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸模組](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 舊版的語言服務提供下列功能︰  
  
|功能|說明|  
|-------------|-----------------|  
|語法標色|會使編輯器檢視來顯示不同的色彩和字型樣式語言的不同元素。 此差異可以輕鬆地讀取與編輯檔案。<br /><br /> 如需一般資訊，請參閱[語法著色舊版語言服務中](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 在受管理的封裝架構 (MPF) 這項功能的相關資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|  
|陳述式完成|完成陳述式或使用者已開始輸入的關鍵字。 陳述式完成可幫助使用者更輕鬆地與少打一些字較少錯誤的機率輸入困難的陳述式。<br /><br /> 如需一般資訊，請參閱[舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|  
|括號對稱|反白顯示成對的大括號等字元。 當使用者輸入結尾字元例如"}"，大括號比對會反白顯示對應的開頭字元，例如"{"。 封入字元數個層級時，這項功能可協助使用者確認正確對應封入字元。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的大括號比對](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。|  
|參數資訊工具提示|會顯示一份可能的使用者目前輸入的多載方法的簽章。<br /><br /> 如需一般資訊，請參閱[舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|  
|錯誤標記|會顯示紅色波浪底線，也就是曲線，底下的語法不正確的文字。 錯誤標記通常可讓使用者察覺的拼字錯誤的關鍵字、 未封閉的括號、 無效的字元和類似的錯誤。<br /><br /> 在 MPF 類別中，錯誤標記會自動處理在<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法的<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別。</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>|  
  
 其中許多功能都需要語言服務剖析原始程式碼。 您通常可以重複使用 token 和剖析程式碼編譯器或解譯器。  
  
 下列功能與程式語言的支援，但不是語言服務的一部分︰  
  
|功能|說明|  
|-------------|-----------------|  
|運算式評估工具|支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過驗證的中斷點，並提供的運算式清單，顯示在偵錯工具**自動變數**偵錯視窗。<br /><br /> 如需詳細資訊，請參閱[語言進行偵錯的服務支援](../../extensibility/internals/language-service-support-for-debugging.md)。|  
|符號瀏覽工具|支援**物件瀏覽器**，**類別檢視**，**呼叫瀏覽器**，和**尋找符號結果**。|
