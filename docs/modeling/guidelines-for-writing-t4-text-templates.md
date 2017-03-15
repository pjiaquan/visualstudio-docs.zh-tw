---
title: "撰寫 T4 文字範本的方針 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 9
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
ms.openlocfilehash: 7d9dd7193455a625b0410eaca3b2bd243c109743
ms.lasthandoff: 02/22/2017

---
# <a name="guidelines-for-writing-t4-text-templates"></a>撰寫 T4 文字範本的方針
這些一般方針可能有助於您在產生程式碼或其他應用程式資源[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它們不被固定的規則。  
  
## <a name="guidelines-for-design-time-t4-templates"></a>設計階段 T4 範本的指導方針  
 設計階段 T4 範本所產生的程式碼的範本程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在設計階段的專案。 如需詳細資訊，請參閱[設計階段使用 T4 文字範本產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 產生的應用程式的變動層面。  
 產生程式碼是最適合這些層面可能會變更專案期間，或將應用程式的不同版本之間變更的應用程式。 分隔開來的這些變動層面更而異的層面，使您可以更輕鬆地判斷哪一個處理序產生。 例如，如果您的應用程式提供的網站，個別服務函式定義從一頁的導覽路徑到另一個邏輯從 [標準] 頁面。  
  
 編碼的一或多個來源模型中的變動層面。  
 模型是檔案或取得的變動部分要產生的程式碼的特定值的每個範本讀取的資料庫。 模型可以是資料庫、 您自己的設計、 圖表或定義域專屬語言的 XML 檔案。 通常，一個模型用來產生許多檔案中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 從另一個範本會產生每個檔案。  
  
 您可以在專案中使用多個模型。 例如，您可以定義網頁和頁面的版面配置的不同模型之間的巡覽的模型。  
  
 使用者的需求和詞彙，而非您的實作，將焦點放在模型。  
 例如，在網站上應用程式中，您應該會參考網頁和超連結的模型。  
  
 在理想情況下，選擇一種適合此模型代表的資訊種類的簡報。 例如，透過網站的導覽路徑的模型，可能是方塊與箭號的圖表。  
  
 測試產生的程式碼。  
 若要確認產生的程式碼可以運作，因為使用者需要使用手動或自動化測試。 避免從相同的模型，從中產生的程式碼產生的測試。  
  
 在某些情況下，一般執行的測試可以在模型上直接。 例如，您可以撰寫的測試，可確保在網站上的每個頁面，可以從任何其他的巡覽到達。  
  
 允許的自訂程式碼︰ 產生部分類別。  
 可讓您撰寫程式碼以手動方式另外產生之程式碼。 很少能夠針對所有可能的變化可能會產生的程式碼產生配置。 因此，您應該預期要新增或覆寫產生的程式碼的部分。 其中所產生的資料是以.NET 語言例如[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，兩種策略會特別有用︰  
  
-   產生的類別應該是部分。 這可讓您將內容加入至產生的程式碼。  
  
-   類別應該產生成對繼承自另一個。 基底類別應該包含所有產生的方法和屬性，而衍生的類別應包含建構函式。 這可讓您手動撰寫的程式碼覆寫任何產生的方法。  
  
 在 XML 等其他產生的語言，使用`<#@include#>`指示詞，即可手動撰寫，並產生內容的簡單的組合。 在更複雜的情況下，您可能必須撰寫結合所產生的檔案與任何手寫檔案後置處理步驟。  
  
 將通用的資料移至包含檔案或執行階段範本  
 若要避免重複的文字和多個範本中的程式碼類似的區塊，使用`<#@ include #>`指示詞。 如需詳細資訊，請參閱[T4 包含指示詞](../modeling/t4-include-directive.md)。  
  
 您可以也建置在個別的專案中，執行階段文字範本，然後呼叫它們從設計階段範本。 若要這樣做，請使用`<#@ assembly #>`指示詞，以存取個別的專案。 如需範例，請參閱[「 繼承在文字範本 」 Gareth Jones 部落格中](http://go.microsoft.com/fwlink/?LinkId=208373)。  
  
 請考慮將大型區塊的程式碼移至不同的組件。  
 如果您有大型的程式碼區塊和類別功能區塊，這十分有用，將此程式碼移到您在個別的專案編譯的方法。 您可以使用`<#@ assembly #>`指示詞，以存取範本中的程式碼。 如需詳細資訊，請參閱[T4 組件指示詞](../modeling/t4-assembly-directive.md)。  
  
 您可以將方法放在範本可以繼承的抽象類別。 抽象類別必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>。</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> 如需詳細資訊，請參閱[T4 範本指示詞](../modeling/t4-template-directive.md)。  
  
 產生程式碼，而不是組態檔案  
 寫入變數的應用程式的一個方法是撰寫可接受組態檔的一般程式碼。 以這種方式撰寫的應用程式非常有彈性，並可以重新設定，而不需重建應用程式的商務需求變更時。 不過，這種方法的缺點是應用程式會執行較少也比其他特定的應用程式。 此外，其程式碼會更難讀取與維護，部分原因是它必須一律處理大部分的泛型型別。  
  
 相較之下，其變動的組件會產生編譯前的應用程式可以是強型別。 這樣可以更容易且更可靠，撰寫手動撰寫程式碼，並將它整合以產生組件的軟體。  
  
 若要取得完整的程式碼產生的好處，嘗試產生程式碼，而不是組態檔案。  
  
 使用產生的程式碼的資料夾  
 將範本和產生的檔案放在專案資料夾名為**產生的程式碼**，讓它清除這些不應該直接編輯的檔案。 如果您建立自訂程式碼來覆寫或加入至產生的類別，將這些類別，名為的資料夾中**自訂程式碼**。 典型的專案結構看起來像這樣︰  
  
```  
MyProject  
   Custom Code  
      Class1.cs  
      Class2.cs  
   Generated Code  
      Class1.tt  
          Class1.cs  
      Class2.tt  
          Class2.cs  
   AnotherClass.cs  
  
```  
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>執行階段 （前置處理過的） T4 範本的指導方針  
 將通用的資料移到繼承的範本  
 您可以使用繼承來共用方法和 T4 文字範本之間的文字區塊。 如需詳細資訊，請參閱[T4 範本指示詞](../modeling/t4-template-directive.md)。  
  
 您也可以使用包含具有執行階段範本檔案。  
  
 將大型程式碼主體移至部分類別。  
 每個執行階段範本會產生具有相同名稱做為範本的部分類別定義。 您可以撰寫程式碼檔案，其中包含另一個部分類別定義的相同。 您可以加入方法、 欄位和建構函式，這種方式中的類別。 從範本中的程式碼區塊可以呼叫這些成員。  
  
 這麼做的優點是程式碼較容易撰寫的因為 IntelliSense 可供使用。 此外，您可以達到更好的呈現方式和基礎邏輯之間的分隔。  
  
 例如，在**MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 在**MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 允許的自訂程式碼︰ 提供擴充點  
 請考慮產生虛擬方法\<#+ 類別功能區塊 #>。 這可讓單一範本使用許多內容，而不需修改。 而不會修改範本，您可以建構在衍生的類別提供的最小的其他邏輯。 在衍生的類別可以是任一個規則的程式碼，或執行階段範本。  
  
 例如，在 MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 在應用程式的程式碼︰  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>所有的 T4 範本的指導方針  
 從文字產生的個別資料收集  
 請盡量避免混合運算和文字區塊。 在每個文字範本中，使用第一個\<封鎖 # # 的程式碼 > 來設定變數並執行複雜的計算。 從第一個文字區塊的範本或第一個值為\<#+ 類別功能區塊 #>，避免長的運算式，並避免迴圈和條件，除非它們包含文字區塊。 這種作法可以讓範本容易讀取與維護。  
  
 請勿使用`.tt`include 檔  
 使用不同的副檔名，例如`.ttinclude`include 檔。 使用`.tt`只針對您想要的檔案處理，並為執行階段或設計階段文字範本。 在某些情況下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]辨識`.tt`檔案，並自動設定其內容以供處理。  
  
 啟動每個範本做為固定的原型。  
 撰寫您要產生，並確定它是正確的程式碼或文字的範例。 然後在變更其副檔名為.tt 和以累加方式插入程式碼會藉由讀取模型修改內容。  
  
 請考慮使用具型別的的模型。  
 雖然您可以建立模型的資料庫或 XML 結構描述，這十分有用來建立網域特定語言 (DSL)。 DSL 的優點是它會產生代表每個節點在結構描述和屬性，以表示屬性的類別。 這表示您可以根據商務模型進行程式設計。 例如：  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 請考慮使用您的模型圖表。  
 許多模型都會最有效地呈現和管理只為文字的資料表，尤其是非常大。  
  
 針對某些類型的商業需求，請務必釐清組複雜的關聯性和工作流程，但圖表都是最適合的媒體。 圖表的優點是，它可以輕易地與使用者和其他專案關係人討論。 藉由從層級的商務需求模型產生程式碼，您將讓您的程式碼為更有彈性，在需求變更時。  
  
 您也可以做為網域特定語言 (DSL) 來設計您自己的圖表類型。 從 UML 和 Dsl，可以產生程式碼。 如需詳細資訊，請參閱[分析和模型化架構](../modeling/analyze-and-model-your-architecture.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)

