---
title: "在舊版語言服務中的語法色彩標示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.contentlocale: zh-tw
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>語法色彩標示在舊版語言服務
語法顏色標示是一種功能，會在不同的色彩和樣式的原始程式檔中顯示的程式語言的不同項目。 若要支援此功能，您需要提供剖析器或掃描器可以識別語彙項目或檔案中的語彙基元的型別。 許多語言關鍵字、 分隔符號 （例如括號或大括號） 來區分及註解標示這些色彩不同的方式。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementation"></a>實作  
 若要支援顏色標示，包括受管理的封裝架構 (MPF)<xref:Microsoft.VisualStudio.Package.Colorizer>類別，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.Package.Colorizer> 這個類別會與互動<xref:Microsoft.VisualStudio.Package.IScanner>來決定的語彙基元和色彩。</xref:Microsoft.VisualStudio.Package.IScanner> 如需有關掃描器的詳細資訊，請參閱[舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別然後標記的色彩資訊的語彙基元的每個字元，並傳回該資訊顯示原始程式檔的編輯器。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 回到編輯器 中的色彩資訊是色彩的項目清單中的索引。 每個色彩的項目指定色彩值和一組字型屬性，例如粗體或刪除線。 編輯器提供一組預設色彩的項目可以使用您語言的服務。 您只需要為指定適當的色彩索引的每個語彙基元的型別。 不過，您可以為權杖，提供一組自訂色彩的項目和您提供的索引，並參考您自己的色彩而不是預設清單的項目清單。 您也必須設定`RequestStockColors`登錄項目設為 0 (或不指定`RequestStockColors`所有項目) 來支援自訂色彩。 您可以設定具名參數，以使用此登錄項目<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>使用者定義的屬性。</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 如需有關註冊語言服務，並設定其選項的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。  
  
## <a name="custom-colorable-items"></a>自訂色彩的項目  
 若要提供您自己的自訂色彩項目，您必須覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>和<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>方法的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 第一個方法會傳回您語言的服務支援的自訂色彩項目數目和第二個取得自訂色彩項目的索引。 您建立自訂色彩的項目預設清單。 語言服務在建構函式，您只需要提供每個色彩項目的名稱。 Visual Studio 會自動處理的情況，其中使用者選取一組不同色彩的項目。 此名稱都會顯示於**字型和色彩**屬性頁上的**選項**對話方塊 (可從 Visual Studio**工具**功能表)，此名稱會決定已覆寫使用者的色彩。 儲存在登錄中快取使用者的選擇，並且色彩名稱來存取。 **字型和色彩**屬性頁面會列出所有的色彩名稱，依字母順序，因此您可以藉由使用您語言的名稱; 每一個色彩名稱前面群組您的自訂色彩，例如 「**TestLanguage 註解**"和"**TestLanguage 關鍵字**」。 您可設定色彩的項目型別，您可以將群組或者 「**註解 (TestLanguage)**"和"**關鍵字 (TestLanguage)**」。 最好使用的語言名稱的群組。  
  
> [!CAUTION]
>  強烈建議您以避免與現有色彩項目的名稱衝突的色彩項目的名稱中包含語言名稱。  
  
> [!NOTE]
>  如果您變更其中一個色彩名稱在開發期間，您必須重設 Visual Studio 建立您的色彩可供存取的第一次快取。 您可以這樣執行**重設實驗 Hive**從 Visual Studio SDK 程式功能表命令。  
  
 請注意色彩的項目清單中的第一個項目永遠不會參考。 Visual Studio 一律會提供的預設文字色彩和該項目的屬性。 最簡單的方式來處理這會提供預留位置色彩項目的第一個項目。  
  
### <a name="high-color-colorable-items"></a>高彩色彩的項目  
 可設定色彩的項目也可支援透過 24 位元或高的色彩值<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>類別支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>標準色彩以及建構函式中指定介面和 24 位元色彩。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.Package.ColorableItem> 請參閱<xref:Microsoft.VisualStudio.Package.ColorableItem>類別，如需詳細資訊。</xref:Microsoft.VisualStudio.Package.ColorableItem> 下列範例示範如何設定關鍵字和註解的 24 位元色彩。 當使用者的桌面，可支援 24 位元色彩使用的 24 位元色彩否則，會使用一般文字色彩。  
  
 請記住，這些是預設的色彩，您的語言。使用者可以變更這些色彩至他們想要的任何內容。  
  
### <a name="example"></a>範例  
 此範例顯示宣告並填入使用<xref:Microsoft.VisualStudio.Package.ColorableItem>類別</xref:Microsoft.VisualStudio.Package.ColorableItem>的自訂色彩項目的陣列的方式 本範例將使用 24 位元色彩的關鍵字和註解色彩。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>色彩標示器類別和掃描器  
 基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別具有<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.Package.Colorizer>類別</xref:Microsoft.VisualStudio.Package.Colorizer>該 instantiantes</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> 傳回從掃描器<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法傳遞給<xref:Microsoft.VisualStudio.Package.Colorizer>類別建構函式。</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
 您必須實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>自己的<xref:Microsoft.VisualStudio.Package.LanguageService>類別</xref:Microsoft.VisualStudio.Package.LanguageService>版本中的方法</xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.Colorizer>類別使用掃描器來取得權杖色彩的所有資訊。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 掃描器必須填入<xref:Microsoft.VisualStudio.Package.TokenInfo>結構的每個權杖，會發現。</xref:Microsoft.VisualStudio.Package.TokenInfo> 此結構包含的資訊，例如範圍語彙基元所佔用的色彩索引，若要使用，是什麼類型的權杖，和權杖觸發程序 (請參閱<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。</xref:Microsoft.VisualStudio.Package.TokenTriggers> 只有範圍和色彩索引所需顏色標示的<xref:Microsoft.VisualStudio.Package.Colorizer>類別。</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 色彩索引儲存在<xref:Microsoft.VisualStudio.Package.TokenInfo>結構通常是介於<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，提供了數個關鍵字和運算子等的各種語言項目相對應的具名索引。</xref:Microsoft.VisualStudio.Package.TokenColor> </xref:Microsoft.VisualStudio.Package.TokenInfo> 如果您自訂色彩的項目清單相符的項目會顯示在<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，則您可以只使用列舉型別做為色彩的每個語彙基元。</xref:Microsoft.VisualStudio.Package.TokenColor> 不過，如果您有其他可設定色彩的項目，或不想使用現有的值的順序，您可以排列您的自訂色彩的項目清單來符合您的需求，並傳回適當的索引為該清單。 只要記得時將其儲存在<xref:Microsoft.VisualStudio.Package.TokenInfo>結構; 轉換要<xref:Microsoft.VisualStudio.Package.TokenColor>索引[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]看到只有索引。 </xref:Microsoft.VisualStudio.Package.TokenColor></xref:Microsoft.VisualStudio.Package.TokenInfo>  
  
### <a name="example"></a>範例  
 下列範例示範如何掃描器可能會識別三個語彙基元的型別︰ 數字、 標點符號和識別項 （任何項目不是數字或標點符號）。 此範例是僅供示範用途，並不代表完整的剖析器和掃描器實作。 它會假設沒有`Lexer`類別`GetNextToken()`方法會傳回字串。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>另請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
