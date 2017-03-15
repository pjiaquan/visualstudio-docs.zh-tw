---
title: "如何...使用文字範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>如何 ... 使用文字範本
文字範本中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供有用的方式來產生任何種類的文字。 您可以使用文字範本產生的文字，做為您的應用程式一部分的執行階段，並在設計階段產生部分專案程式碼。 本主題摘要說明最常詢問"How do I …？ 」 問題。  
  
 本主題中，項目符號前面有多個答案是替代的建議。  
  
 文字範本的一般簡介，讀取[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
## <a name="how-to-"></a>如何...  
  
### <a name="generate-part-of-my-application-code"></a>產生應用程式程式碼的一部分  
 我有一個組態或*模型*檔案或資料庫中。 我的程式碼的一個或多個組件相依於該模型。  
  
-   從文字範本會產生一些程式碼檔案。 如需詳細資訊，請參閱[設計階段使用 T4 文字範本產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)和[開始撰寫範本的最佳方式為何？](#starting)。  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>在執行階段，將資料傳入範本產生檔案  
 在執行階段，我的應用程式會產生文字檔案，例如包含混合的標準文字和資料的報表。 我想要避免撰寫數百個`write`陳述式。  
  
-   將執行階段文字範本加入至您的專案。 此範本建立程式碼，您可以具現化，並使用產生的文字中的類別。 您可以將資料傳遞給它建構函式參數。 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
-   如果您想要產生從只有在執行階段可用的範本，您可以使用標準文字範本。 如果您要撰寫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組，您可以叫用文字範本化服務。 如需詳細資訊，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。 在其他內容中，您可以使用文字範本引擎。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     使用\<#@parameter#> 將參數傳遞給這些範本指示詞。 如需詳細資訊，請參閱[T4 參數指示詞](../modeling/t4-parameter-directive.md)。  
  
### <a name="read-another-project-file-from-a-template"></a>從範本讀取另一個專案檔  
 若要讀取檔案的同一個[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]做為範本的專案︰  
  
-   將 `hostSpecific="true"` 插入至 `<#@template#>` 指示詞。  
  
     在程式碼中，使用`this.Host.ResolvePath(filename)`來取得檔案的完整路徑。  
  
### <a name="invoke-methods-from-a-template"></a>叫用方法，從範本  
 如果方法已存在，比方說，標準[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別︰  
  
-   使用\<#@assembly#> 指示詞，以載入組件，並使用\<#@import#> 來設定命名空間內容。 如需詳細資訊，請參閱[T4 匯入指示詞](../modeling/t4-import-directive.md)。  
  
     如果您經常使用相同的組件匯入指示詞，請考慮撰寫指示詞處理器。 在每個範本中，您可以叫用指示詞處理器，來載入組件和模型檔案和設定的命名空間內容。 如需詳細資訊，請參閱[建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
 如果您要自行撰寫的方法︰  
  
-   如果您正在撰寫執行階段文字範本中，撰寫具有同名的執行階段文字範本的部分類別定義。 這個類別中加入額外的方法。  
  
-   寫入類別功能控制區塊`<#+ ... #>`在其中您可以宣告的方法、 屬性和私用類別。 文字範本編譯時，會將它轉換為類別。 標準控制區塊`<#...#>`文字會轉換為單一方法和類別功能區塊會插入做為個別成員。 如需詳細資訊，請參閱[文字範本控制區塊](../modeling/text-template-control-blocks.md)。  
  
     定義為類別功能也可以包含內嵌的文字區塊的方法。  
  
     考慮將放在不同的檔案，您可以在類別功能`<#@include#>`到一或多個範本檔案。  
  
-   在不同的組件 （類別程式庫） 中撰寫方法，並從您的範本呼叫它們。 使用`<#@assembly#>`指示詞，以載入組件，以及`<#@import#>`設定命名空間內容。 請注意，若要在偵錯時，請重建組件，您可能必須停止並重新啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[T4 文字範本指示詞](../modeling/t4-text-template-directives.md)。  
  
### <a name="generate-many-files-from-one-model-schema"></a>從一個模型結構描述產生多個檔案  
 如果您通常會從具有相同的資料庫或 XML 結構描述模型產生檔案︰  
  
-   請考慮撰寫指示詞處理器。 這可讓您將多個組件陳述式和匯入每個範本，使用單一自訂指示詞中的陳述式。 指示詞處理器也可以載入和剖析模型檔案。 如需詳細資訊，請參閱[建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)。  
  
### <a name="generate-files-from-a-complex-model"></a>從複雜的模型產生檔案  
  
-   請考慮建立定義域專屬語言 (DSL) 來代表模型。 這讓您更容易撰寫範本，因為您使用型別和屬性會反映在模型中項目的名稱。 您不必在剖析該檔案，或瀏覽 XML 節點。 例如:   
  
     `foreach (Book book in this.Library) { ... }`  
  
     如需詳細資訊，請參閱[開始使用定義域專屬語言](../modeling/getting-started-with-domain-specific-languages.md)和[定義域專屬語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>取得資料[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 若要使用中提供的服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，由組`hostSpecific`屬性，並載入`EnvDTE`組件。 例如：  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>在建置程序中執行文字範本  
  
-   如需詳細資訊，請參閱[建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。  
  
## <a name="more-general-questions"></a>一般問題  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>若要開始撰寫文字範本的最佳方式為何？  
  
1.  寫入產生的檔案的特定範例。  
  
2.  將它轉換成文字範本中，插入`<#@template #>`指示詞，指示詞和程式碼會載入所需的輸入的檔或模型。  
  
3.  漸進式運算式和程式碼區塊取代檔案的部分。  
  
### <a name="what-is-a-model"></a>「 模型 」 是什麼？  
  
-   範本所讀取的輸入。 可能是在檔案或資料庫中。 它可能是 XML，或 Visio 繪圖，或網域特定語言 (DSL) 或 UML 模型中，或可能是純文字。 它可以分散到多個檔案。 通常一個以上的範本會讀取一個模型。  
  
     「 模型 」 一詞的含意是企業的，它代表某方面更直接比產生的程式碼或其他檔案。 比方說，它可能會代表您產生的軟體將會負責通訊網路的計劃。  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>使用文字範本的好處是什麼？  
 一般而言，您可以從一個模型產生多個程式碼或其他檔案。 模型產生的程式碼比直接在呈現需求。 它省略了實作詳細資料，並根據需求，而非程式碼會寫入。 當需求變更 – 一樣通常 – 您可以更輕鬆且更可靠的程式碼的不同部分比更新模型。  
  
 程式碼產生，因此是從 agile 開發方法的觀點來看的寶貴工具。  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>「 最佳作法 」 還有哪些文字範本？  
  
-   如需詳細資訊，請參閱[撰寫 T4 文字範本的指導方針](../modeling/guidelines-for-writing-t4-text-templates.md)。  
  
### <a name="what-is-t4"></a>什麼是 「 T4 」？  
  
-   另一個名稱[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]此處所述的文字範本功能。 舊的版本中，未發行的 「 文字範本轉換 」 的縮寫。

