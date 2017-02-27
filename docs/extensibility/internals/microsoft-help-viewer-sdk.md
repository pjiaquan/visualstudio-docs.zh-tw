---
title: "Microsoft 說明檢視器 SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Microsoft 說明檢視器 SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這篇文章包含 Visual Studio 說明檢視器整合者執行下列工作:  
  
-   建立主題 \(F1 支援\)  
  
-   建立說明檢視器內容商標套件  
  
-   部署文件的集  
  
-   加入說明 Visual Studio shell \(整合模式或獨立模式\)  
  
-   其他資源  
  
### 建立主題 \(F1 支援\)  
 本節提供的形式呈現的主題、 主題需求、 如何建立主題 \(包括 F1 支援需求\)，最後，範例主題，以其呈現結果的簡短描述元件的概觀。  
  
 **說明檢視器主題概觀**  
  
 主題呈現呼叫時，說明檢視器取得品牌的安裝或上次更新，以及主題 XHTML，當時可能會與主題相關聯的封裝元素，並結合這兩個導致呈現內容的檢視 \(商標資料 \+ 主題資料\)。  商標的套件包含標誌、 內容的行為和商標文字 \(版權等\) 的支援。  如下 「 建立品牌封裝 」 品牌封裝元素的詳細資訊。  萬一沒有商標與主題相關聯的封裝，說明檢視器會使用後援說明檢視器應用程式根目錄 \(Branding\_en US.mshc\) 中的商標設定封裝。  
  
 **說明檢視器主題需求**  
  
 若要正確呈現在說明檢視器中，原始的主題內容必須是 W3C 基本 1.1 XHTML。  
  
 主題通常包含兩個區段:  
  
-   中繼資料 \(請參閱內容的中繼資料參考\): 資料有關的主題，例如，主題的唯一識別碼，關鍵字值，目錄識別碼的主題父節點識別碼，依此類推。  
  
-   本文內容: 與 W3C 基本 1.1 XHTML 相容，包括支援內容的行為 \(可摺疊區域中，程式碼片段等。完整清單如下所示\)。  
  
 Visual Studio 品牌套件支援的控制項:  
  
-   連結  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   繼承的成員  
  
-   LanguageSpecificText  
  
 支援的語言字串 \(不區分大小寫\):  
  
-   javascript  
  
-   csharp 或 c\#  
  
-   cplusplus visualc \+ \+ 或 c \+ \+  
  
-   jscript  
  
-   visual basic 或 vb  
  
-   f \# fsharp 或 fs  
  
-   其他 – 代表的語言名稱的字串  
  
 **建立主題說明檢視器**  
  
 建立新的 XHTML 文件，名為 ContosoTopic4.htm，並包含在 title 標記 \(如下\)。  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 接下來，將資料加入至定義如何呈現 \(本身品牌與否\)，本主題的方式來參考本主題的 f1 鍵，本主題所在目錄中，其識別碼 \(適用於其他主題的連結參考\) 內，等等。請參閱 \< 支援的中繼資料的完整清單下方的 「 內容中繼資料 」 資料表。  
  
-   在此情況下，我們將使用我們自己的商標設定封裝，Visual Studio 說明檢視器的商標設定封裝的 variant。  
  
-   新增 F1 中繼名稱和值 \(「 Microsoft.Help.F1 」 內容 \="ContosoTopic4"\)，會比對 IDE 屬性包中提供的 F1 值。  \(請參閱 F1 支援部分以取得詳細資訊\)。   這是比對，F1 的值從 ide 即可顯示這個主題在 IDE 中選擇 f1 鍵時所呼叫。  
  
-   新增主題識別碼。 這是由連結到本主題的其他主題的字串。  它是本主題說明檢視器識別碼。  
  
-   目錄中，加入本主題父節點，來定義這個主題 TOC 節點會出現的位置。  
  
-   目錄中，加入本主題的節點順序。 當父節點有 n 個子節點時，定義子節點順序本主題的位置。 例如，本主題是 4 子主題的數字 4。\)  
  
 範例中繼資料 \> 一節:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **主題內容**  
  
 本文的主題 \(不包括頁首和頁尾\) 將包含頁面所連結的、 注意 \> 一節、 可摺疊的區域、 程式碼片段和語言特定的文字區段。  請參閱商標取得這些區域的形式呈現的主題的資訊。  
  
1.  新增主題標題標記:  `<div class="title">Contoso Topic 4</div>`  
  
2.  新增附註區段: `<div class="alert"> add your table tag and text </div>`  
  
3.  新增可摺疊的區域:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  加入程式碼片段:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  加入程式碼的語言特定的文字:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` 請注意該 devLangnu \= 可讓您輸入其他語言。 例如，devLangnu \="Fortran 」 將會顯示 Fortran 時程式碼片段 DisplayLanguage \= Fortran  
  
6.  加入頁面的連結: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意: 不支援新 「 顯示語言 」 \(例如，F \#、 Cobol、 Fortran\) 的程式碼顏色標示程式碼片段中的將單色。  
  
 **範例說明檢視器主題** 的程式碼說明如何定義中繼資料、 程式碼片段，可摺疊的區域和語言特定的文字。  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **F1 支援**  
  
 在 Visual Studio 中，選取 F1 會產生從 IDE 內的資料指標的位置所提供的值並於其中填入 「 屬性包 」 為提供的值 \(根據資料指標位置。 當游標位於功能 x 時，功能 x 是作用中\/單元的焦點，並填入屬性包與值。  選取 F1 時填入屬性包，以及 Visual Studio F1 程式碼會尋找客戶的預設說明來源是否為本機或線上 \(線上是預設值\)，然後建立適當的字串為基礎的使用者設定 \(線上是預設值\) – 殼層執行 \(請參閱說明系統管理員指南的 exe 啟動參數\) 使用本機說明檢視器 \+ 關鍵字，從屬性包，如果本機說明是預設值的參數或 MSDN URL 的參數清單中的關鍵字。  
  
 如果三個字串所傳回的 F1，稱為為多重值字串時，請在第一個詞彙，尋找為叫用，以及如果找到，我們已經完成。否則，請移至下一個字串。  順序很重要。 多重值關鍵字的呈現方式應該是最長的字串，以最短的字串。  若要驗證這一點，如果是多重值的關鍵字，看看線上 F1 URL 字串，其中包含所選的關鍵字。  
  
 在 Visual Studio 2012 中，我們刻意更強的除以之間建立線上和離線時，這樣如果使用者的設定為線上，然後我們只要 F1 要求直接傳遞至我們的線上查詢服務 MSDN，而不是我們在 Visual Studio 2010 協助程式庫代理程式透過路由傳送。 我們再仰賴的狀態 」 安裝廠商內容 \= true"以判斷是否有不同的內容中。 如果為 true，我們再執行此剖析和路由邏輯，根據您想要為您的客戶支援。 如果為 false，然後我們就前往 MSDN。 如果是本機使用者的設定，則所有呼叫只要都移至本機說明引擎。  
  
 F1 流程圖表:  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 當說明檢視器的預設說明內容來源設定為 \[線上 \(啟動瀏覽器中\):  
  
-   Visual Studio 合作夥伴 \(VSP\) 功能發出 F1 屬性包 \(屬性包 prefix.keyword 和線上 URL 在登錄中找到的前置詞\) 的值: F1 傳送 VSP URL \+ 參數至瀏覽器。  
  
-   Visual Studio 功能 \(語言編輯器、 Visual Studio 特定功能表項目等\): F1 將 Visual Studio URL 傳送到瀏覽器。  
  
 當說明檢視器的預設說明內容來源設定為本機說明 \(Help 檢視器中啟動\):  
  
-   F1 屬性包與本機存放區索引之間的關鍵字相符的 VSP 功能 \(也就是屬性包 prefix.keyword \= 本機存放區索引中找到的值\): F1 轉譯說明檢視器中的主題。  
  
-   Visual Studio 功能 \(若要覆寫從 Visual Studio 功能所發出的屬性包 VSP 任何選項\): F1 呈現 Visual Studio 中的主題說明檢視器。  
  
 設定下列登錄值以啟用 F1 後援廠商的說明內容。 F1 後援表示線上說明檢視器設定為尋找 F1 說明內容，而且廠商內容在本機上安裝使用者的硬碟。 即使預設設定是線上說明的說明檢視器應該查看本機說明內容。  
  
1.  設定 **VendorContent** 協助 2.1 登錄機碼下的值:  
  
    -   32 位元作業系統:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword: 00000001  
  
    -   64 位元作業系統:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword: 00000001  
  
2.  註冊夥伴命名空間協助 2.1 登錄機碼之下:  
  
    -   32 位元作業系統:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< 命名空間 \>*  
  
         「 位置 」 \= 「 離線 」  
  
    -   64 位元作業系統:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< 命名空間 \>*  
  
         「 位置 」 \= 「 離線 」  
  
 **剖析的基底原生命名空間**  
  
 若要開啟剖析基底的原生命名空間，在登錄中加入新的 DWORD 的名稱: BaseNativeNamespaces 並設定其值為 1 \(下他們想要支援的型錄金鑰\)。  例如，如果您想要使用 Visual Studio 類別目錄，您無法將金鑰的路徑:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 當標頭\/方法時發現格式 F1 關鍵字時，'\/' 字元將會被剖析，導致下列建構:  
  
-   標頭: 將會是可用來在登錄中登錄的命名空間  
  
-   方法: 這會成為取得通過的關鍵字。  
  
 例如，假設一個稱為 CustomLibrary 的自訂程式庫和方法時將會格式化為 F1 要求傳入呼叫 MyTestMethod， `CustomLibrary/MyTestMethod`。  
  
 使用者可以註冊 CustomLibrary 為命名空間底下夥伴，並提供任何位置索引鍵，並傳遞給查詢的關鍵字會 MyTestMethod。  
  
 **啟用偵錯工具在 IDE 中的說明**  
  
 新增下列登錄機碼和值:  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic 說明鍵: 顯示偵錯輸出零售值: \[是\]  
  
 在 IDE 中，在 \[說明\] 功能表項目中，選取 \[偵錯協助內容\]  
  
 **內容的中繼資料**  
  
 下表中出現在括號之間的任何字串是一個預留位置，必須以可辨識的值取代。 例如，在 \< 中繼 name\="Microsoft.Help.Locale 」 內容 \="在 \[語言\]"\/ \>，「 \[語言程式碼\] 」 必須取代值，例如 「 en\-us\-我們 」。  
  
|屬性 \(HTML 表示\)|描述|  
|--------------------|--------|  
|\< 中繼 name\="Microsoft.Help.Locale 」 內容 \="在 \[語言\-\]"\/ \>|本主題的地區設定。 如果此標記用在主題中，必須只執行一次使用，它必須插入上述任何 Microsoft 說明標記。 如果未使用此標記，本主題的內文是藉由指定; 如果是產品地區設定相關聯的斷詞工具編製索引否則，en\-us\-我們會使用斷詞工具。 此標記會符合 ISOC RFC 4646。 若要確保 Microsoft 說明可正確運作，使用這個屬性而不是一般的 \[語言\] 屬性。|  
|\< 中繼 name\="Microsoft.Help.TopicLocale 」 內容 \="在 \[語言\-\]"\/ \>|本主題的地區設定時也會使用其他地區設定。 如果此標記用在主題中，它必須使用只執行一次。 類別目錄包含一個以上的語言中的內容時，請使用這個標記。 在目錄中的多個主題可以有相同的識別碼，但每個必須指定唯一的 TopicLocale。 指定符合目錄的地區設定 TopicLocale 這個主題會顯示在目錄中的主題。 不過，所有語言版本的主題會都顯示在搜尋結果中。|  
|\< 標題 \> \[標題\] \< \/ t \>|指定本主題的標題。 此標記是必要的而且必須用於主題的只執行一次。 如果主題的本文不包含標題 \< d i v \> 區段，這個標題會顯示在主題中，並在目錄中。|  
|\< 中繼名稱 \="Microsoft.Help.Keywords"內容 \="\[aKeywordPhrase\]"\/ \>|指定連結的說明檢視器中的 \[索引\] 窗格中顯示的文字。 按一下連結時，會顯示主題。您可以指定多個索引關鍵字的主題，或如果您不想要顯示在索引中這個主題的連結，可以略過此標記。 "K"關鍵字，從較早版本的說明可以轉換成這個屬性。|  
|\< 中繼 name\="Microsoft.Help.Id 」 內容 \="\[TopicID\]"\/ \>|設定本主題的識別碼。 此標記是必要的而且必須用於主題的只執行一次。 識別碼必須在目錄中的主題，相同的地區設定中的唯一性。 在另一個主題中，您可以建立本主題的連結，使用此識別碼。|  
|\< 中繼 name\="Microsoft.Help.F1"content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|指定本主題的 f1 說明關鍵字。 您可以指定多個 F1 關鍵字的主題，或如果不想讓應用程式使用者按下 F1 時顯示本主題，您可以省略這個標記。 通常，只有一個 F1 關鍵字會指定主題。 "F"關鍵字，從較早版本的說明可以轉換成這個屬性。|  
|\< 中繼名稱 \="Description"內容 \="\[主題 description\]"\/ \>|提供本主題中的內容的簡短摘要。 如果此標記用在主題中，它必須使用只執行一次。 由查詢程式庫中，直接存取此屬性它不會儲存在索引檔案。|  
|\< 中繼 name\="Microsoft.Help.TocParent 」 內容 \="\[sys.internal\_tables\]"\/ \>|指定的父主題本主題中的目錄。 此標記是必要的而且必須用於主題的只執行一次。 此值為父代的 Microsoft.Help.Id。 主題可以有內容的資料表中只有一個位置。 "\-1"會被視為目錄根的主題識別碼。 在 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], ，該頁面是說明檢視器\] 首頁。 這是我們特別將 TocParent \= 1 加入一些主題，以確保這些項目顯示在上方層級相同的原因。說明檢視器\] 首頁上是系統\] 頁面上，因此不可取代。 如果 VSP 嘗試新增的頁面識別碼為\-1 時，它可能會新增到內容集，但說明檢視器一律會使用系統頁面\-說明檢視器首頁|  
|\< 中繼 name\="Microsoft.Help.TocOrder 」 內容 \="\[正整數\]"\/ \>|指定的目錄中本主題出現的位置相對於其對等主題。 此標記是必要的而且必須用於主題的只執行一次。 值為整數。 指定數值較小整數的主題會顯示指定的較高值的整數的主題上方。|  
|\< 中繼 name\="Microsoft.Help.Product 」 內容 \="\[product code\]"\/ \>|指定此主題描述的產品。 如果此標記用在主題中，它必須使用只執行一次。 這項資訊也可提供做為參數傳遞給協助索引子。|  
|\< 中繼 name\="Microsoft.Help.ProductVersion 」 內容 \="\[版本號碼\]"\/ \>|指定此主題描述的產品版本。 如果此標記用在主題中，它必須使用只執行一次。 這項資訊也可提供做為參數傳遞給協助索引子。|  
|\< 中繼 name\="Microsoft.Help.Category 」 內容 \="\[string\]"\/ \>|用來識別子內容的產品。 您可以識別多個小節的主題，或如果您不想找出任何小節的連結，可以略過此標記。 此標記用來儲存 TargetOS 和 TargetFrameworkMoniker 的屬性，當轉換從較早版本的說明主題。 內容的格式是 AttributeName:AttributeValue。|  
|\< 中繼 name\="Microsoft.Help.TopicVersion 內容 \="\[主題版本號碼\]"\/ \>|在目錄中的多個版本存在時，請指定此版本的主題。 Microsoft.Help.Id 不保證是唯一的因為此標記時需要多個版本的主題是指在目錄中，例如，目錄的.NET Framework 3.5、 一個主題包含主題的.NET Framework 4 和兩者都有相同的 Microsoft.Help.Id。|  
|\< 中繼名稱 \="SelfBranded"內容 \="\[TRUE 或 FALSE\]"\/ \>|指定這個主題使用 Help Library 管理員啟動商標或商標套件的特定主題。 此標記必須是 TRUE 或 FALSE。 如果它，則為 TRUE，商標套件相關聯的主題會覆寫商標 Help Library 管理員啟動，以便讓主題呈現如預期般，即使它不同於其他內容的呈現時所設定的封裝。 如果是 FALSE，目前的主題會轉譯根據品牌 Help Library 管理員啟動時設定的封裝。 根據預設，Help Library 管理員假設自我品牌除非 SelfBranded 變數宣告為 TRUE; 否則為 false因此，您不需要宣告 \< 中繼名稱 \="SelfBranded"內容 \="FALSE"\/ \>。|  
  
### 建立商標的套件  
 Visual Studio 版本包含許多不同的 Visual Studio 產品，包括 Visual Studio 合作夥伴的隔離和整合式的 shell。  每一個這些產品需要某種程度的主題為基礎的說明內容商標唯一產品支援。  例如，Visual Studio 主題需要有一致的品牌簡報，而 SQL Studio 中，以包裝 ISO 殼層，則需要使用它自己唯一說明內容的商標的每個主題。  整合式 Shell 合作夥伴可能會想要在 Visual Studio 產品的說明內容的父系同時維護自己的主題商標其 \[說明\] 主題。  
  
 商標的套件會安裝包含說明檢視器的產品。  適用於 Visual Studio 產品:  
  
-   說明檢視器 2.1 應用程式根目錄中安裝後援商標封裝 \(Branding\_ \< 地區設定 \>.mshc\) \(範例: C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\)，說明檢視器語言組件。  這用於未安裝這兩項產品商標套件的情況下 \(已安裝任何內容\) 或已安裝的商標套件已損毀的位置。  請注意，使用應用程式根目錄後援商標套件時，會忽略的 Visual Studio 項目 \(標誌和意見反應\)。  
  
-   Visual Studio 內容安裝時從內容封裝服務，商標套件也會安裝 \(適用於第一個階段的內容安裝案例\)。  商標的套件的更新時下, 一步的內容更新或其他封裝的安裝動作發生時，已安裝更新。  
  
 Microsoft 說明檢視器支援主題主題中繼資料為基礎的商標。  
  
-   主題中繼資料其中定義自我品牌 \= true、 呈現主題現況，不執行任何動作 \(儘商標\)。  
  
-   主題中繼資料其中定義自我品牌 \= false，使用商標 TopicVendor 中繼資料值相關聯的套件。  
  
-   其中主題中繼資料定義 name\="Microsoft.Help.TopicVendor 」 內容 \= \< 商標套件名稱廠商 MSHA \>，請使用商標的套件中的內容值定義。  
  
-   請注意，Visual Studio 類別目錄中，有優先順序應用程式的商標的套件。  套用第一個 Visual Studio 預設商標，並接著，如果主題中繼資料中定義，而且支援與相關聯的商標封裝 \(如安裝 msha 中所定義\)，套用覆寫版本的廠商定義。  
  
 品牌元素通常分為三個主要類別:  
  
-   \(範例包括意見反應連結、 條件式免責聲明文字、 標誌\) 的標頭項目  
  
-   內容 \(範例包括展開\/摺疊控制項文字的項目和程式碼片段項目\) 的行為  
  
-   頁尾項目 \(例如著作權\)  
  
 視為品牌的元素所包含的項目 \(此規格中詳細說明\):  
  
-   目錄\/產品標誌 \(例如，Visual Studio\)  
  
-   意見反應連結和電子郵件項目  
  
-   免責聲明文字  
  
-   著作權文字  
  
 支援的檔案中的 Visual Studio 說明檢視器商標套件包括:  
  
-   圖形 \(標誌、 圖示\)  
  
-   Branding.js – 指令碼檔案支援內容的行為  
  
-   Branding.xml – 一致地用於目錄內容的字串。  注意: Visual Studio 中 branding.xml 當地語系化文字項目包含 \_locID \= 「 \< 唯一值 \> 」  
  
-   Branding.css – 簡報一致性的樣式定義  
  
-   Printing.css – 一致的列印呈現的樣式定義  
  
 如上所述，商標套件是與主題相關聯:  
  
-   當 SelfBranded \= false 已定義的中繼資料中，本主題會繼承目錄商標套件  
  
-   或當 SelfBranded \= false 和那里唯一的商標封裝以 MSHA 和定義可用時安裝內容  
  
 如 Vsp 實作自訂品牌的封裝 \(VSP 內容，SelfBranded \= True\)，繼續執行的一種方法是啟動後援商標套件 \(安裝說明檢視器\)，並將變更的檔案名稱。  Branding\_ \< 地區設定 \>.mshc 檔案是 zip 檔案副檔名變更為.mshc 檔案，因此只要從.mshc 將副檔名變更為.zip 然後再將內容解壓縮。  商標封裝元素，請參閱下面的並視需要修改 \(例如，VSP 標誌和商標 Branding.xml 檔案中的參考變更的標誌、 Branding.xml 更新每個 VSP 細節等\)。  
  
 完成所有修改，請建立包含所需的品牌元素的 zip 檔案，並將副檔名變更為.mshc。  
  
 若要將自訂商標的套件，建立包含商標 mshc 檔案以及內容 \(包含的主題\) 的 mshc 參考 MSHA。  請參閱下方如何建立基本 MSHA 「 MSHA 」。  
  
 Branding.xml 檔案包含用於一致地呈現在主題中的特定項目時，本主題中的清單項目 \< 中繼 name\="Microsoft.Help.SelfBranded 」 內容 \="false"\/ \>。  Visual Studio 清單 Branding.xml 檔案中的項目如下所示。  請注意，這份清單可以用來做為範本的 ISO 殼層採用他們用來修改這些項目 \(例如標誌、 意見反應及著作權\) 以符合他們自己產品商標的需求。  
  
 附註: 註明"{n}"的變數擁有程式碼相依性，移除或變更這些值會造成錯誤，而且可能是應用程式當機。Visual Studio 品牌封裝中包含當地語系化的識別項 \(範例 \_locID\="codesnippet.n 」\)。  
  
 **Branding.xml**  
  
|||  
|-|-|  
|功能:|**CollapsibleArea**|  
|請使用:|展開摺疊內容控制項文字|  
|**項目**|**值**|  
|ExpandText|展開|  
|CollapseText|摺疊|  
|功能:|**CodeSnippet**|  
|請使用:|控制項的程式碼片段的文字。  注意: 空間將會變更 「 非中斷 」 空間的程式碼片段內容。|  
|**項目**|**值**|  
|CopyToClipboard|複製至剪貼簿|  
|ViewColorizedText|檢視|  
|CombinedVBTabDisplayLanguage|Visual Basic \(範例\)|  
|VBDeclaration|宣告|  
|VBUsage|使用量|  
|功能:|**意見反應、 頁尾及標誌**|  
|請使用:|提供意見反應控制項，為客戶提供意見反應透過電子郵件目前的主題。  著作權文字內容。  標誌的定義。|  
|**項目**|**值 \(這些字串可以修改以符合內容採納者需要\)。**|  
|著作權|© 2013 Microsoft Corporation。 著作權所有，並保留一切權利。|  
|SendFeedback|\< a \="{0}"\\{1\\} \> 傳送意見反應 \<\/a \> 意見傳送至 Microsoft。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|功能:|**免責聲明**|  
|請使用:|案例的特定免責聲明機器的一組翻譯內容。|  
|**項目**|**值**|  
|MT\_Editable|這篇文章已轉譯的機器。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|MT\_NonEditable|這篇文章已轉譯的機器。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|MT\_QualityEditable|這篇文章是人工翻譯。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|MT\_QualityNonEditable|這篇文章是人工翻譯。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|MT\_BetaContents|這篇文章是機器翻譯的初步版本。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|MT\_BetaRecycledContents|這篇文章是人工翻譯初步版本。 如果您有網際網路連線時，選取在同一時間，與原始英文內容的可編輯模式下檢視此頁面的 \[檢視線上本主題\]。|  
|功能:|**LinkTable**|  
|請使用:|如需線上主題的連結的支援|  
|**項目**|**值**|  
|LinkTableTitle|連結資料表|  
|TopicEnuLinkText|檢視您的電腦上可以使用本主題的英文版 \<\/a \>。|  
|TopicOnlineLinkText|檢視本主題 \< href \="{0}"\\{1\\} \> 線上的 \<\/a \>|  
|OnlineText|線上|  
|功能:|**視訊的音訊控制項**|  
|請使用:|顯示項目和視訊內容的文字|  
|**項目**|**值**|  
|MultiMediaNotSupported|必須安裝 Internet Explorer 9 或更新版本支援 {0} 內容。|  
|VideoText|顯示視訊|  
|AudioText|串流處理音訊|  
|OnlineVideoLinkText|\< p \> 若要檢視與本主題中，關聯的視訊，請按 {0} \< href \="\\\\ {1 \\\\}"\> \\{2\\}here \<\/a \>。 \<\/p \>|  
|OnlineAudioLinkText|\< p \> 若要聆聽的音訊與本主題中，相關聯，請按 {0} \< href \="\\\\ {1 \\\\}"\> \\{2\\}here \<\/a \>。 \<\/p \>|  
|功能:|**未安裝的內容控制項**|  
|請使用:|用於 contentnotinstalled.htm 轉譯文字元素 \(字串\)|  
|**項目**|**值**|  
|ContentNotInstalledTitle|找不到您的電腦上的任何內容。|  
|ContentNotInstalledDownloadContentText|\< p \> 若要將內容下載到您的電腦，\< href \="{0}"\\{1\\} \> \[管理\] 索引標籤 \<\/a \>。 \<\/p \>|  
|ContentNotInstalledText|\< p \> 無內容被安裝在電腦上。 請參閱您的系統管理員本機說明內容的安裝。 \<\/p \>|  
|功能:|**主題找不到控制項**|  
|請使用:|用於 topicnotfound.htm 轉譯文字元素 \(字串\)|  
|**項目**|**值**|  
|TopicNotFoundTitle|在您的電腦上找不到要求的主題。|  
|TopicNotFoundViewOnlineText|\< p \> 您所要求的主題找不到您的電腦上，但是您可以 \< a \="{0}"\\{1\\} \> 檢視主題線上 \<\/a \>。 \<\/p \>|  
|TopicNotFoundDownloadContentText|\< p \> 請參閱瀏覽窗格，針對類似主題的連結或 \< href \="{0}"\\{1\\} \> 按一下 \[管理\] 索引標籤 \<\/a \> 若要將內容下載到您的電腦。 \<\/p \>|  
|TopicNotFoundText|\< p \> 您所要求的主題找不到您電腦上。 \<\/p \>|  
|功能:|**主題已損毀的控制項**|  
|請使用:|用於 topiccorrupted.htm 轉譯文字元素 \(字串\)|  
|**項目**|**值**|  
|TopicCorruptedTitle|無法顯示要求的主題。|  
|TopicCorruptedViewOnlineText|\< p \> 說明檢視器 」 無法顯示要求的主題。 可能的主題的內容或基礎系統相依性。 \<\/p \> 發生錯誤|  
|功能:|**首頁上的控制項**|  
|請使用:|支援說明檢視器的最上層節點內容的顯示文字。|  
|**項目**|**值**|  
|HomePageTitle|說明檢視器首頁|  
|HomePageIntroduction|\< p \> 歡迎使用 Microsoft 說明檢視器，為不可或缺的每一位使用者使用 Microsoft 工具、 產品、 技術和服務的資訊來源。 說明檢視器可讓您存取方法和參考的資訊、 範例程式碼、 技術文章等等。 若要尋找需要請瀏覽目錄的內容，請使用全文檢索搜尋或瀏覽的內容關鍵字索引。 \<\/p \>|  
|HomePageContentInstallText|\< p \>\< b \/ \> 使用 \< href \="{0}"\\{1\\} \> 管理內容 \<\/a \> 索引標籤上，執行下列動作: \< u l \>\< i \> 新增內容至您的電腦。 \<\/l i \>\< i \> 檢查更新本機內容。 \<\/l i \>\< i \> 從您的電腦。 \<\/l i \>\< \/ u l \>\< \/ p \> 中移除內容|  
|HomePageInstalledBooks|已安裝的書籍|  
|HomePageNoBooksInstalled|找不到您的電腦上的任何內容。|  
|HomePageHelpSettings|說明內容設定|  
|HomePageHelpSettingsText|\< p \> 您目前的設定是本機說明。 說明檢視器會顯示您已安裝在電腦的內容 \< b \/ \> 若要變更的來源的說明內容，在 Visual Studio 功能表列上，選擇 \[\< s p a n style \="{0}"\> 協助，請設定說明偏好 \< \/ s p a n \>。 \< b \/ \>\< \/ p \>|  
|Mb|MB|  
  
 **branding.js**  
  
 Branding.js 檔案包含 Visual Studio 說明檢視器品牌元素所使用的 JavaScript。  以下是品牌元素和支援的 JavaScript 函式的清單。  此檔案的頂端 」 可當地語系化的字串 \> 一節中定義這個檔案要當地語系化的所有字串。  請注意 ICL 檔案已建立的 branding.js 檔案內的當地語系化字串。  
  
||||  
|-|-|-|  
|**商標功能**|**JavaScript 函式**|**描述**|  
|Var...||定義變數|  
|取得使用者程式碼語言|setUserPreferenceLang|對應索引 \# 程式碼語言|  
|設定並取得 cookie 值|getCookie setCookie||  
|繼承的成員|changeMembersLabel|展開\/摺疊繼承的成員|  
|當 SelfBranded \= False|onLoad|讀取的查詢字串來檢查它是否為列印要求。  設定所有 codesnippets 專注使用者慣用的索引標籤。  如果是列印要求然後將 isPrinterFriendly 設定為 true。 檢查有高對比模式。|  
|程式碼片段|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|將所有的可摺疊控制項物件寫清單。|  
||CA\_Click|可摺疊的區域的狀態為基礎，用來定義哪些影像和文字呈現|  
|標誌的對比支援|isBlackBackground\(\)|呼叫以判斷背景是否為黑色。  精確時，才在高對比模式。|  
||isHighContrast\(\)|使用色彩的範圍來偵測高對比模式|  
||onHighContrast\(black\)|呼叫時偵測到高對比|  
|LST 功能|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|多媒體功能|標題 \(開始、 結束時，文字樣式\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(styleName、 styleValue\)||  
||showCC\(id\)||  
||subtitle\(id\)||  
  
 **HTM 檔案**  
  
 商標的套件包含一組支援的金鑰進行資訊通訊說明內容的使用者，例如首頁，其中包含描述的內容集所安裝的區段和頁面的主題本機集合中找不到主題時，告訴使用者案例的 HTM 檔。 請注意這些 HTM 檔案，可以修改每項產品。  ISO 殼層廠商是可以採取預設商標套件和變更的行為與這些網頁的內容套件需要。  這些檔案會參考其個別的商標套件，才能將商標的標記，以獲得 branding.xml 檔案的相對應的內容中。  
  
||||  
|-|-|-|  
|**檔案**|**用法**|**顯示內容來源**|  
|homepage.htm|這是一個頁面會顯示目前已安裝的內容，並適當呈現給使用者，其內容相關的任何其他訊息。  此檔案具有額外的中繼資料屬性 」 Microsoft.Help.Id 」 內容 \="\-1"，而放置這頂端本機內容目錄的內容。||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.xml，標記 \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.xml，標記 \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.xml，標記 \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|標題區段 Branding.xml 標記 \< HomePageInstalledBooks \>，從應用程式，\< HomePageNoBooksInstalled \> 沒有書籍安裝時產生的資料。|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|標題 Branding.xml 標記 \< HomePageHelpSettings \>，區段文字 \< HomePageHelpSettingsText \> 一節。|  
|topiccorrupted.htm|主題存在於本機設定，但無法顯示因為某些原因 \(損毀的內容\)。||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.xml，標記 \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.xml，標記 \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|當主題找不到本機內容中設定，也可以使用線上||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.xml，標記 \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.xml、 標記 \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.xml，標記 \< TopicNotFoundText \>|  
|contentnotinstalled.htm|當沒有本機安裝的產品內容。||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.xml，標記 \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.xml，標記 \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.xml，標記 \< ContentNotInstalledText \>|  
  
 **CSS 檔案**  
  
 Visual Studio 說明檢視器商標套件包含兩個 css 檔案，以支援一致的 Visual Studio 說明內容呈現:  
  
-   Branding.css – 包含 css 項目來呈現 where SelfBranded \= false  
  
-   Printer.css – 包含 css 項目來呈現 where SelfBranded \= false  
  
 Branding.css 檔案包含 Visual Studio 主題簡報的定義 \(一點，可能會變更包含在封裝服務從 Branding\_ \< 地區設定 \>.mshc branding.css\)。  
  
 **圖形檔案**  
  
 Visual Studio 內容顯示 Visual Studio 標誌及其他圖形。  Visual Studio 說明檢視器商標套件中的圖形檔案的完整清單如下所示。  
  
||||  
|-|-|-|  
|**檔案**|**用法**|**範例**|  
|clear.gif|用來呈現可摺疊的區域||  
|footer\_slice.gif|頁尾簡報||  
|info\_icon.gif|用來顯示資訊|免責聲明|  
|online\_icon.gif|這個圖示是要與線上連結產生關聯||  
|tabLeftBD.gif|用來呈現程式碼片段容器||  
|tabRightBD.gif|用來呈現程式碼片段容器||  
|vs\_logo\_bk.gif|用於一般的對比標誌參考 Branding.xml 標記 \< LogoFileName \> 中所定義。  適用於 Visual Studio 產品商標名稱為 vs\_logo\_bk.gif。||  
|vs\_logo\_wh.gif|用於一般高標誌參考 Branding.xml 標記 \< LogoFileNameHC \> 中所定義。  適用於 Visual Studio 產品商標名稱為 vs\_logo\_wh.gif。||  
|ccOff.png|隱藏式字幕功能的圖形||  
|ccOn.png|隱藏式字幕功能的圖形||  
|ImageSprite.png|用來呈現可摺疊的區域|展開或摺疊圖形|  
  
### 部署一系列主題  
 這是既簡單又快速的教學課程，建立說明檢視器內容部署設定組成 MSHA 檔案和封包組或 MSHC 所含的主題。 描述一組的 cab 檔案的 XML 檔案或 MSHC 檔案 MSHA。 說明檢視器可以讀取 MSHA 取得清單的內容 \(。封包或。MSHC 檔案\) 可供本機安裝。  
  
 這是描述非常基本的 XML 結構描述的說明檢視器 MSHA 基礎課程。  請注意，範例實作下面這個簡短的概觀和範例 HelpContentSetup.msha。  
  
 此入門，基於 MSHA 的名稱是的 HelpContentSetup.msha \(檔案名稱可以是任何擴充功能。MSHA\)。 HelpContentSetup.msha \(下面的範例\) 應該包含 cab 或 MSHCs 可用的清單。  請注意，必須一致 \(不支援 MSHA 和 CAB 檔案類型的組合\) MSHA 內的檔案類型。 針對每個封包或 MSHC，應該會有 \< v class \= 「 套件 」 \>...\< \/ d i v \> \(請參閱下面範例\)。  
  
 注意: 在實作下列範例中，包含商標的套件。 這是重要包括以取得所需的 Visual Studio 內容呈現項目和內容的行為。  
  
 範例 \[HelpContentSetup.msha\] 檔案: \(取代 」 內容集名稱是 1 」 和 「 內容集名稱 2 」 等等，都是與您的檔案名稱。\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  建立本機資料夾，就像 「 C:\\SampleContent 」  
  
2.  此範例中，我們將使用 MSHC 檔案包含的主題。  MSHC 是 zip 變更以.zip 副檔名。MSHC。  
  
3.  建立以下 HelpContentSetup.msha 為文字檔 \(用來建立檔案 \[記事本\]\) 並將它儲存到上面所述的資料夾 \(請參閱步驟 1\)。  
  
 請注意，「 商標 」 存在，而且是唯一的類別。 商標 mshc 併入此入門，使已安裝的內容將會有商標 MSHCs 中所包含的內容行為會有商標的套件中包含的適當的支援項目。 沒有這麼做，系統會針對不屬於擷取 \(安裝\) 的支援項目內容時，會導致錯誤。  
  
 若要取得 Visual Studio 品牌封裝，將複製到您的工作資料夾的 Branding\_en US.mshc 檔案中的，於 C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\。  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **總結**  
  
 使用及擴充上述步驟將會啟用 Vsp 部署 Visual Studio 說明檢視器及其內容的集合。  
  
### 將說明加入至 Visual Studio Shell \(整合模式和獨立模式\)  
 **簡介**  
  
 本逐步解說示範如何併入 Visual Studio Shell 應用程式中的說明內容，然後再加以部署。  
  
 **需求**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 隔離 Shell 可轉散發套件](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **概觀**  
  
 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 殼層是新版 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE 的基底應用程式。 這類應用程式包含您所建立的延伸模組以及獨立的 Shell。 使用獨立 Shell 專案範本包含在 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK 建置擴充功能。  
  
 建立獨立 Shell 為基礎的應用程式和其說明的基本步驟:  
  
1.  取得 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell 可轉散發套件 \(Microsoft 下載\)。  
  
2.  在 Visual Studio 中，建立說明延伸模組為基礎的獨立 Shell，比方說，Contoso 說明擴充本逐步解說稍後所述。  
  
3.  擴充功能和可轉散發 MSI \(應用程式安裝程式\) 部署到 ISO 殼層會換行。 本逐步解說中不包含設定步驟。  
  
 建立 Visual Studio 內容存放區。 整合式 Shell 案例中，變更視覺化 Studio12 產品類別目錄名稱，如下所示:  
  
-   建立資料夾 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12。  
  
-   建立名為 CatalogType.xml 的檔案，並將它加入至資料夾。 此檔案應該包含下列程式碼行:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 在登錄中定義的內容存放區。 整合式 Shell 中，變更 VisualStudio12 產品類別目錄名稱:  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     索引鍵: LocationPath 字串值: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     索引鍵: CatalogName 字串值: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 文件  
  
 **建立專案**  
  
 若要建立獨立 Shell 擴充功能:  
  
1.  在 Visual Studio 中，在 **檔案**, ，選擇 **新的專案**, 下 **其他專案類型** 選擇 **擴充性**, ，然後選擇 \[  **Visual Studio Shell 外掛式主控**。 將專案命名為 `ContosoHelpShell`\) 來建立 Visual Studio 隔離 Shell 範本為基礎的擴充性專案。  
  
2.  在 \[方案總管在 ContosoHelpShellUI 專案中，在資源檔的資料夾中，開啟 ApplicationCommands.vsct。 請確定這一行註解 \(搜尋 「 No\_Help 」\): `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  選擇 F5 鍵以編譯並執行 **偵錯**。 在隔離的殼層 IDE 的實驗執行個體，選擇 \[ **協助** 功能表。 請確定 **檢視說明**, ，**加入和移除說明內容**, ，和 **設定說明偏好** 命令會出現。  
  
4.  在 \[方案總管在 ContosHelpShell 專案中，在自訂殼層資料夾中，開啟 ContosoHelpShell.pkgdef。 若要定義 Contoso 說明目錄中，加入下列幾行:  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  在 \[方案總管在 ContosHelpShell 專案中，在自訂殼層資料夾中，開啟 ContosoHelpShell.Application.pkgdef。 若要啟用 F1 說明，請加入下列程式碼行:  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  在 \[方案總管的 ContosoHelpShell 方案時，內容功能表上選擇 **屬性** 功能表項目。 在 **組態屬性**, ，請選取 **Configuration Manager**。 在 **組態** 資料行，將每個 「 偵錯 」 的值變更為 「 發行 」。  
  
7.  建置方案。 這將在下一節中使用的發行資料夾中建立一組檔案。  
  
 若要進行測試，如果部署:  
  
1.  在電腦上您要部署 Contoso，若要安裝下載的 ISO 殼層 \(from above\)。  
  
2.  建立資料夾的 \\\\Program Files \(x86\) \\，並將其命名 `Contoso`。  
  
3.  從 ContosoHelpShell 發行資料夾的內容複製到 \\\\Program Files \(x86\) \\Contoso\\ 資料夾中。  
  
4.  選擇啟動登錄編輯程式  **執行** 中 **啟動** \] 功能表上，輸入 `Regedit`。 在 \[登錄編輯器中，選擇 \[ **檔案**, ，然後 **匯入**。 瀏覽至 ContosoHelpShell 專案資料夾。 在 ContosoHelpShell 子資料夾中，選擇 ContosoHelpShell.reg。  
  
5.  建立內容存放區:  
  
     ISO shell\-建立 Contoso 內容存放區 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12  
  
     如 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 整合式 Shell、 建立資料夾 C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  建立 CatalogType.xml 並新增要包含的內容存放區 \(上一個步驟\):  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  新增下列登錄機碼:  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: LocationPath 字串值:  
  
     ISO 殼層:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 整合式的 Shell:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     索引鍵: CatalogName 字串值: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 文件。 ISO 殼層，這是您目錄的名稱。  
  
8.  將您的內容 \(cab 或 MSHC 和 MSHA\) 複製到本機資料夾。  
  
9. 進行測試的內容存放區整合式 Shell 命令列範例。 ISO 殼層變更適當地比對產品的類別目錄和 launchingApp 值。  
  
     "C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe"\/catalogName VisualStudio12 \/helpQuery 方法 \= 」 頁面與 id \= ContosoTopic0"\/launchingApp Microsoft visual Studio，12.0  
  
10. 啟動 Contoso 應用程式 \(來自 Contoso 應用程式根目錄中\)。 在 ISO 殼層中，選擇 \[ **協助** 功能表項目，以及變更 **設定說明偏好** 至 **使用本機說明**。  
  
11. 在殼層中，選擇 \[ **協助** 功能表項目，然後 **檢視說明**。 本機說明檢視器應該啟動。 選擇 \[管理內容\] 索引標籤。 在 **安裝來源**, ，選擇 \[ **磁碟** 選項按鈕。 選擇 **...** 按鈕並瀏覽至包含 \[Contoso 內容 \(複製到上一個步驟中的本機資料夾\) 的本機資料夾。 選擇 \[HelpContentSetup.msha\]。 Contoso 應該顯示為活頁簿中的活頁簿選取項目中。 選擇 **新增**, ，然後選擇 \[ **更新** 按鈕 \(右上角的底部\)。  
  
12. 在 Contoso IDE 中，選擇 F1 鍵，以測試 F1 功能。  
  
### 其他資源  
 執行階段 API，請參閱 [Windows 說明 API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。  
  
 如需有關如何運用說明 API 的詳細資訊，請參閱 [說明檢視器程式碼範例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 若要提供意見反應這些元件，請使用 [Microsoft Connect](http://connect.microsoft.com/)。  
  
 請提交功能建議 [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 若要取得其他說明，請嘗試 [MSDN 開發人員文件和說明系統論壇](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 更新的重大問題，請參閱 [說明檢視器讀我檔案](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 若要直接連絡說明檢視器 PM 小組，傳送電子郵件給 hlpfdbk@microsoft.com