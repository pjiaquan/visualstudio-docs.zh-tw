---
title: "在編輯器內 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的架構"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
caps.handback.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
---
# 在編輯器內
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

編輯器\] 是由數個不同子系統，設計用來將編輯器文字檢視和使用者介面文字模型分開。  
  
 下列各節說明編輯器\] 中的不同層面︰  
  
-   [子系統的概觀](../extensibility/inside-the-editor.md#overview)  
  
-   [文字模型](../extensibility/inside-the-editor.md#textmodel)  
  
-   [文字檢視](../extensibility/inside-the-editor.md#textview)  
  
 下列各節說明編輯器\] 中的功能︰  
  
-   [標記和分類器](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [裝飾](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projection](../extensibility/inside-the-editor.md#projection)  
  
-   [大綱](../extensibility/inside-the-editor.md#outlining)  
  
-   [滑鼠繫結](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [編輯器作業](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> 子系統的概觀  
  
### 文字模型子系統  
 文字模型子系統負責代表文字，並啟用其操作。 文字模型子系統包含 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 介面，其中描述編輯器所顯示的字元序列。 這段文字可以修改、 追蹤，和其他方式操作它在許多方面。 文字模型提供的類型的下列層面︰  
  
-   將文字相關聯的檔案，並管理讀取和寫入檔案系統中的服務。  
  
-   尋找物件的兩個序列之間的最小差異差異服務。  
  
-   系統，用於描述方面的其他緩衝區中的文字子集的緩衝區中的文字。  
  
 文字模型子系統是免費的使用者介面 \(UI\) 的概念。 比方說，它並不負責文字格式或文字版面配置和它並不知道可能會與文字相關的視覺裝飾。  
  
 文字模型子系統的公用型別都包含在 Microsoft.VisualStudio.Text.Data.dll 和 Microsoft.VisualStudio.CoreUtilitiy.dll，只會依賴.NET Framework 基底類別程式庫和 Managed Extensibility Framework \(MEF\)。  
  
### 文字檢視子系統  
 文字檢視子系統負責格式化及顯示文字。 此子系統中的型別分為兩個圖層上，根據型別是否依賴 Windows Presentation Foundation \(WPF\)。 最重要的型別是 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 和 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, ，可控制要顯示的文字行的集合，也插入號、 選取項目和功能，在文字裝飾使用 WPF UI 項目。 此子系統也提供文字周圍的邊界顯示區域。 這些邊界可加以擴充，而且可以包含不同類型的內容和視覺效果。 邊界的範例包括列數字的顯示和捲軸。  
  
 文字檢視子系統的公用型別都包含在 Microsoft.VisualStudio.Text.UI.dll 和 Microsoft.VisualStudio.Text.UI.Wpf.dll。 第一個組件包含這些平台無關的項目，而第二個包含 WPF 特定項目。  
  
### 分類子系統  
 分類子系統負責決定文字的字型屬性。 分類器會將文字分成不同類別，例如 「 關鍵字 」 或 「 註解 」。 分類格式對應與這些類別實際的字型屬性，例如，「 藍色 Consolas 10 pt"。 文字檢視格式，呈現文字時，使用這項資訊。 標記，稍後在本主題中，詳細說明，這是讓資料相關聯的文字。  
  
 分類子系統的公用型別會包含在 Microsoft.VisualStudio.Text.Logic.dll，而且它們分類，其包含在 Microsoft.VisualStudio.Text.UI.Wpf.dll 的視覺效果與互動。  
  
### 作業子系統  
 作業子系統定義編輯器行為。 它提供 Visual Studio 編輯器命令的實作和復原系統。  
  
## 探討文字模型和文字檢視  
  
###  <a name="textmodel"></a> 文字模型  
 文字模型子系統所組成的文字型別不同群組。 其中包括文字緩衝區、 文字快照集，以及文字範圍。  
  
#### 文字緩衝區和文字的快照集  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 介面代表的使用 utf\-16，也就是編碼所使用編碼的 Unicode 字元序列 `String` .NET Framework 中的類型。 文字緩衝區可以保存為檔案系統的文件，但這並非必要條件。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 用來建立一個空白文字的緩衝區或從字串或初始化文字緩衝區 <xref:System.IO.TextReader>。 文字緩衝區可以保存至檔案系統做為 <xref:Microsoft.VisualStudio.Text.ITextDocument>。  
  
 文字緩衝區可以編輯的任何執行緒，直到執行緒接管文字緩衝區呼叫 <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>。 之後，只有該執行緒可以執行編輯。  
  
 文字緩衝區可能經過許多版本，在其存留期間。 每次編輯緩衝區，並不變，會產生新的版本 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 代表該版本之緩衝區的內容。 因為文字快照集是固定不變，您就可以存取文字上的快照集不使用限制的任何執行緒，即使它所代表的文字緩衝區持續變更。  
  
#### 文字的快照集和快照集程式碼文字行  
 為一串字元或一連串的程式碼行，您可以檢視文字快照集內容。 行數和字元是兩者索引 0 開始。 空白文字快照集包含零個字元和一個空白行。 任何有效 Unicode 換行字元序列，或是開頭或結尾的緩衝區，會分隔一條線。 換行字元會明確表示文字的快照集，並不是所有具有相同文字快照中的分行符號。  
  
> [!NOTE]
>  如需 Visual Studio 編輯器中的換行字元的詳細資訊，請參閱 [編碼與分行符號](../ide/encodings-and-line-breaks.md)。  
  
 文字行由 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 物件，可從文字的快照集的特定行號或特定的字元位置。  
  
#### SnapshotPoints、 SnapshotSpans 和 NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> 代表快照中的字元位置。 位置一定會介於 0 和快照集的長度。 A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 代表一段文字中的快照集。 結束位置一定會介於 0 和快照集的長度。<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 組成一組 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 從相同的快照集的物件。  
  
#### 範圍和 NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> 間隔可套用的一段文字快照中的文字。 快照集位置都以零起始，因此範圍可以在任何包含零的位置。`End` 的 span 屬性的總和等於其 `Start` 屬性及其 `Length` 屬性。 A `Span` 不包含字元編製索引 `End` 屬性。 比方說，有開始一段 \= 5 且長度 \= 3 的結束 \= 8，以及在位置 5、 6 和 7 個字元。 此範圍內的表示法是非 5..8）。  
  
 兩個範圍交集，如果有任何位置，包括結束的位置。 因此的交集 \[3, 5\) 和 \[2, 7\) 是 \[3, 5\) 和交集的 \[3, 5\) 和 \[5, 7\) 為 \[5，5）。 \(請注意，\[5，5\) 是空的範圍。\)  
  
 兩個範圍重疊，才位置相同，除了結束位置。 空的 span 永遠不會重疊任何其他範圍內，並不會是空的兩個範圍重疊。  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 是範圍的範圍開始屬性順序的清單。 在清單中，會合併重疊或相鄰的範圍。 例如，假設是範圍的集合 \[5..9\)，\[0..1\)，\[3..6\)，和 \[9..10\)，正規化的清單的範圍是 \[0..1\)，\[3..10\)。  
  
#### ITextEdit、 TextVersion 和文字變更通知  
 可以變更文字緩衝區的內容使用 <xref:Microsoft.VisualStudio.Text.ITextEdit> 物件。 建立這類物件 \(使用其中一種 `CreateEdit()` 方法 <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) 啟動文字交易組成的文字編輯內容。 編輯每個屬性的某些段字串緩衝區中的文字取代。 座標和每個編輯的內容會表示相對於緩衝區的快照集交易啟動時。<xref:Microsoft.VisualStudio.Text.ITextEdit> 物件調整編輯受影響的其他編輯同一筆交易中的座標。  
  
 文字緩衝區，其中包含這個字串為例︰  
  
```  
abcdefghij  
```  
  
 套用交易，其中包含兩個編輯、 取代在範圍內的一個編輯 \[2..4\) 使用的字元 `X` 並取代在範圍內的第二個編輯 \[6..9\) 使用的字元 `Y`。 結果是這個緩衝區︰  
  
```  
abXefYj  
```  
  
 在套用第一次編輯之前，進行第二個編輯座標所計算的交易，開頭緩衝區的內容。  
  
 緩衝區所做的變更才會生效時 <xref:Microsoft.VisualStudio.Text.ITextEdit> 承諾物件呼叫其 `Apply()` 方法。 如果沒有至少一個非空白的編輯、 新 <xref:Microsoft.VisualStudio.Text.ITextVersion> 建立時，新 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 建立時，和一個 `Changed` 就會引發事件。 每個文字版本的不同文字快照集。 文字的快照集之後編輯異動，表示文字緩衝區的完成狀態，但文字版說明只變更從一個快照集下一步\]。 一般情況下，文字快照集是適用於一次後即捨棄，雖然有時候，文字版本必須保持存留。  
  
 文字版包含 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 這個集合會描述所做的變更，套用至快照集時，將會產生後續的快照集。 每個 <xref:Microsoft.VisualStudio.Text.ITextChange> 集合中包含的變更、 取代的字串，並取代字串的字元位置。 取代的字串是空的是基本的插入和取代字串是空的基本刪除。 正規化的集合一律都是 `null` 文字緩衝區的最新版本。  
  
 只有一個 <xref:Microsoft.VisualStudio.Text.ITextEdit> 可以具現化物件的文字緩衝區，任何時候，必須擁有文字緩衝區 （如果宣告的擁有權） 的執行緒上執行所有的文字編輯內容。 編輯文字，可以藉由呼叫已放棄其 `Cancel` 方法或其 `Dispose` 方法。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 也提供 `Insert()`, ，`Delete()`, ，和 `Replace()` 類似的方法上找到 <xref:Microsoft.VisualStudio.Text.ITextEdit> 介面。 呼叫這些具有相同的效果建立 <xref:Microsoft.VisualStudio.Text.ITextEdit> 物件，進行類似的呼叫，然後套用編輯。  
  
#### 追蹤點和追蹤範圍  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> 代表文字緩衝區中的字元位置。 如果緩衝區已編輯的方式會造成要移動的字元位置，追蹤點會與它轉移。 例如，如果追蹤點是指位置 10 在緩衝區中，而且緩衝區的開頭會插入五個字元，追蹤點那麼參考到 15 個。 如果插入的情況發生在精確地表示追蹤點的位置，其行為取決於其 <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, ，這可以是 `Positive` 或 `Negative`。 如果追蹤模式是正數，追蹤點指的是相同的字元現在是在結尾插入。如果追蹤模式為負數，追蹤點是指到原始位置插入的第一個字元。 如果刪除由追蹤點位置的字元，則追蹤點會移到後面的已刪除的範圍的第一個字元。 例如，如果追蹤點是指在位置 5 的字元位置 3 到 6 個字元會被刪除，追蹤點是指 3 位置處的字元。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 代表一連串字元，而不是只有一個位置。 其行為取決於其 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>。 如果 n 追蹤模式是 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，追蹤範圍成長納入邊緣; 在插入的文字，如果 span 的追蹤模式是 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，追蹤範圍不會加入插入其邊緣的文字。 不過，如果 span 的追蹤模式是 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，插入將目前位置推入朝開始時，如果 span 的追蹤模式 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ，插入推送到結尾的目前位置。  
  
 您可以取得文字緩衝區，其所屬的任何快照集的追蹤點的位置或追蹤範圍的範圍。 追蹤點和追蹤範圍可安全地參考從任何執行緒。  
  
#### 內容類型  
 內容類型是內容的一種機制來定義不同類型。 內容類型可以是檔案類型，例如 「 文字 」、 「 程式碼 」 或 「 二進位 」 或技術類型，例如"xml"、"vb"或"c\#"。 例如，word 「 using 」 是關鍵字在 C\# 和 Visual Basic 中，但不是在其他程式設計語言。 因此，此關鍵字的定義會受限於"c\#"和"vb"的內容類型。  
  
 內容類型可做為篩選條件的裝飾和其他項目的編輯器\] 中。 許多編輯器功能和擴充點定義每個內容類型。例如，文字著色是不同的純文字檔、 XML 檔案和 Visual Basic 原始程式碼檔。 文字緩衝區通常指派內容的類型時建立，且可以變更文字緩衝區的內容類型。  
  
 內容類型可以多\-繼承自其他內容類型。<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 可讓您指定多個基底型別為指定的內容類型的父系。  
  
 開發人員可以定義自己的內容類型，並使用這些登錄 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>。 許多編輯器功能，可以使用來定義特定的內容類型方面 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。 例如，編輯器邊界、 裝飾和滑鼠處理常式可以定義，使它們只適用於顯示特定內容類型的編輯器。  
  
###  <a name="textview"></a> 文字檢視  
 模型檢視控制器 \(MVC\) 模式的檢視部分定義文字檢視中，檢視表，例如捲軸，以及插入號圖形元素的格式。 Visual Studio 編輯器中的所有簡報項目是以 WPF 為都基礎。  
  
#### 文字檢視  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 介面是文字檢視的平台無關的表示方式。 它主要用來顯示文字文件，在視窗中，但它也可用用於其他用途，例如，在工具提示。  
  
 文字檢視參考不同種類的文字緩衝區。<xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> 屬性是指 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 指向這些三個不同的文字緩衝區物件︰ 資料緩衝區，也就是最上層的資料層級緩衝區編輯緩衝區中編輯，而且 visual 緩衝區，也就是顯示在文字檢視中的緩衝區。  
  
 文字格式根據附加到基礎文字緩衝區中，分類器，而且會裝飾使用附加至文字檢視本身的裝飾提供者。  
  
#### 文字檢視座標系統  
 文字檢視座標系統中指定的文字檢視中的位置。 在此座標系統， x 值 0.0 會對應至所顯示之文字的左邊緣和 y 值 0.0 會對應到頂端所顯示的文字。 x 協調從左到右的增加而 y 協調增加從上到下。  
  
 檢視區 （在文字視窗中顯示的文字部分） 無法水平捲動的相同方式為垂直捲動。 因此，它對於繪圖介面就會變更其左方的座標水平捲動檢視區。 不過，在檢視區可以垂直捲動只能透過變更所呈現的文字，會導致 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 引發事件。  
  
 座標系統中的距離會對應至邏輯像素為單位。 如果文字轉譯介面會顯示不縮放轉換，則文字轉譯座標系統中的一個單位對應於在螢幕上顯示一個像素。  
  
#### 邊界  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> 介面表示邊界，並啟用可見性的邊界和其大小的控制。 有四個預先定義的邊界，也就名為"Top"、 「 左 」、 「 右 」 和 「 下方 」，而連接到頂端、 底部、 左邊或右邊的檢視。 這些邊界是可以在其中放置其他邊界的容器。 介面會定義傳回邊界的大小和邊界的可見性的方法。 邊界會提供其他資訊附加至文字檢視的視覺元素。 例如，行號邊界會顯示文字檢視的行號。 圖像邊界會顯示 UI 項目。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 介面會處理建立和邊界的位置。 邊界可以相對於其他邊界來排序。 較高優先權邊界位於更接近文字檢視。 例如，如果有兩個左邊的界，邊界的邊界 B，邊界 B 具有較低的優先順序比邊界的邊界 B 會左邊界 A.  
  
#### 文字檢視主應用程式  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 介面包含文字檢視和任何相鄰的裝飾隨附的檢視，比方說，捲軸。 文字檢視主應用程式也包含已附加至檢視的框線的邊界。  
  
#### 格式化的文字  
 文字檢視中顯示的文字組成 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 物件。 每個文字檢視行對應到另一行文字檢視中的文字。 長基礎文字緩衝區中的程式可以部分 （如果未啟用自動換行） 會被遮住或分成多個文字檢視程式碼行。<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 介面包含方法和屬性對應座標之間的字元，以及可能會以列相關聯的裝飾。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 物件可由使用 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 介面。 如果您只關心目前檢視中顯示的文字時，您可以忽略格式設定的來源。 如果您想要在不是文字的格式顯示在檢視 （例如，若要支援 rtf 文字剪下和貼上），您可以使用 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 來格式化文字緩衝區中的文字。  
  
 文字檢視格式一 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 一次。  
  
## 編輯器功能  
 編輯器的功能設計，因此功能的定義是不同於它的實作。 編輯器包含下列功能︰  
  
-   標記和分類器  
  
-   裝飾  
  
-   Projection  
  
-   大綱  
  
-   滑鼠和索引鍵繫結  
  
-   作業和基本項目  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> 標記和分類器  
 標記是一段文字相關聯的標記。 他們可以看到不同的方式，例如，使用文字著色、 底線、 圖形或快顯視窗。 分類器是一種標記。  
  
 其他類型的標記則 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 來反白顯示文字， <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 的大綱、 和 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 的編譯錯誤。  
  
#### 分類的類型  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 介面表示等價類別是抽象類別的文字。 分類類型可以多\-繼承自其他類別類型。 例如，程式設計語言分類可能包含 「 關鍵字 」、 「 註解 」 和 「 識別碼 」，它們全都繼承自 「 程式碼 」。 自然語言分類類型可能包括 「 名詞 」、 「 動詞命令 」 和 「 形容詞 」，它們全都繼承自 「 自然語言 」。  
  
#### 類別  
 分類是特定類別類型的執行個體通常會透過一段文字。 A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 用來代表一種分類。 分類範圍可以視為涵蓋特定的一段文字，並告訴系統的特定類別類型，此段文字的標籤。  
  
#### 分類器  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 是一種機制，分成一組分類的文字。 必須為特定內容類型定義，針對特定文字緩衝區具現化分類器。 用戶端必須實作 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 參與文字分類。  
  
#### 分類彙總工具  
 分類的彙總工具是一種機制，將一個文字緩衝區的所有分類器結合成一組分類。 例如，C\# 分類和英文語言分類器可以透過 C\# 檔案中的註解建立分類。 請考慮此註解︰  
  
```  
// This method produces a classifier  
```  
  
 C\# 類別器可能會標記為註解，整個範圍和英文語言分類可能分類 」 產生 「 做為 「 動作 」 和 「 方法 」 為 「 名詞 」。 彙總工具會產生一組非重疊的分類和集的類型根據所有成果。  
  
 分類的彙總工具也是分類器，因為文字分成一組分類。 有任何重疊的分類和分類的排序，也可確保分類彙總工具。 個別的分類器是免費以任何順序，傳回任何分類，一組並以任何方式重疊。  
  
#### 分類格式和文字色彩  
 文字格式是文字分類為基礎之功能的範例。 它可用來判斷應用程式中的文字的顯示文字檢視層。 文字格式化區域依存於 WPF 中，但邏輯定義的分類並不會。  
  
 分類格式是一組格式化特定分類類型的內容。 這些格式會繼承父系的分類類型格式。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 是從分類類型會對應至一組文字格式設定屬性。 在編輯器中的格式對應的實作會處理分類格式的所有的匯出。  
  
###  <a name="adornments"></a> 裝飾  
 裝飾會直接與無關的字型和色彩的文字檢視中的字元的圖形效果。 例如，用來標記非編譯程式碼，在許多程式設計語言中，紅色曲線底線是內嵌的裝飾，而工具提示則為快顯的裝飾。 裝飾衍生自 <xref:System.Windows.UIElement> 和實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 有兩種裝飾標記的特殊的類型 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, ，如佔據相同的空間，以在檢視中，文字的裝飾和 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, ，曲線的底線的。  
  
 內嵌的裝飾會形成部分格式化的文字檢視的圖形。 組織在不同的疊置順序圖層。 有三個內建的層級的如下所示︰ 文字、 插入號，並選取項目。 不過，開發人員可以定義多個圖層，並將它們放在彼此的相對順序。 內嵌裝飾的三種為相對於文字裝飾 （這移動時文字會移動，並刪除文字時，刪除），相對於檢視裝飾 （這是要檢視的非文字部分） 和擁有者控制的裝飾 （開發人員必須管理它們的位置）。  
  
 快顯裝飾是一個小型視窗上方的文字檢視，例如工具提示中顯示圖片的。  
  
###  <a name="projection"></a> Projection  
 投影是建構文字緩衝區，不會實際儲存的文字，但改為結合其他文字緩衝區中的文字不同的技巧。 比方說，投影緩衝區可以用來串連兩個其他緩衝區中的文字，並呈現結果，它是在只有一個緩衝區，或是隱藏的同一個緩衝區中的文字部分。 投影緩衝區可做為另一個投影緩衝區之來源緩衝區。 一組相關的投影的緩衝區可以建構以各種方式重新排列的文字。 \(這類集也就是 *緩衝區圖形*。\) Visual Studio 文字大綱功能由實作來隱藏摺疊的文字，使用投影的緩衝區，Visual Studio 編輯器中的 ASP.NET 網頁使用投影來支援內嵌的 Visual Basic 和 C\# 等語言。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 由使用 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>。 投影緩衝區由已排序的 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 物件，稱為 *來源範圍*。 這些範圍的內容會呈現為一串字元。 所繪製來源範圍的文字緩衝區會命名為 *來源緩衝區*。 投影緩衝區的用戶端並沒有要注意，不同於一般文字緩衝區。  
  
 投影緩衝區接聽來源緩衝區大小的文字變更事件。 當來源中的文字範圍內的變更時，投影緩衝區已變更的文字座標會對應至它自己的座標，並引發適當的文字變更事件。 例如，請考慮這些內容的來源緩衝區 A 和 B:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 如果投影緩衝區 P 形成的兩個文字範圍，其中一個，其中包含所有緩衝區，而其他所有緩衝區 B、 P 有以下內容︰  
  
```  
P: ABCDEvwxyz  
```  
  
 如果子字串 `xy` 刪除從緩衝區 B，則緩衝區 P 引發事件，表示已刪除的字元位置 7 和 8。  
  
 也可以直接編輯投影緩衝區。 它會傳播對適當的來源緩衝區。 例如，如果插入的字串緩衝區 P 位置 6 （"v"字元的原始位置），插入的動作就會傳播到緩衝區 B 位於位置 1。  
  
 有參與投影緩衝區來源範圍的限制。 來源範圍可能不會重疊。投影緩衝區中的位置無法對應至多個位置中任何來源緩衝區，而來源緩衝區中的位置無法對應到投影緩衝區中的多個位置。 來源緩衝區關聯性中，也允許沒有 circularities。  
  
 來源組緩衝投影緩衝區變更和來源組跨越變更時，會引發事件。  
  
 Elision 緩衝區是一種特殊的投影緩衝區。 它主要用大綱及展開和摺疊的文字區塊的作業。 Elision 緩衝區根據單一來源緩衝區，並 elision 緩衝區中的範圍的順序必須相同，它們的順序中的來源緩衝區。  
  
##### 緩衝的圖形  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 介面可讓投影緩衝區的圖形之間的對應。 導向非循環圖，非常相似的語言編譯器所產生的抽象語法樹狀目錄中收集的所有文字緩衝區和投影緩衝區。 圖形會定義最上層的緩衝區，它可以是任何文字緩衝區。 從來源緩衝區中的點上的緩衝區中的點或一組的來源緩衝區中的範圍內最上層緩衝區中的範圍，可以將對應緩衝區圖形。 同樣地，它可以對應點，或從來源緩衝區跨越到最上層的緩衝區中的點。 緩衝的圖形會建立使用 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>。  
  
##### 事件和投影緩衝區  
 修改投影緩衝區時，所做的修改會從投影緩衝區傳送至依存於此的緩衝區。 修改所有緩衝區之後，會引發緩衝區變更事件，從最深的緩衝區。  
  
###  <a name="outlining"></a> 大綱  
 大綱是文字的展開或摺疊的不同文字檢視中區塊的能力。 大綱定義為一種的 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, ，在相同的方式與裝飾所定義。 A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 是定義可以展開或摺疊的文字區域的標記。 若要使用大綱，您必須匯入 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> 取得 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大綱 manager 列舉、 摺疊，並展開不同的區塊，表示為 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 物件，並據以產生的事件。  
  
###  <a name="mousebindings"></a> 滑鼠繫結  
 滑鼠繫結至不同的命令連結滑鼠動作。 您可以使用滑鼠繫結定義 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, ，使用已定義的索引鍵繫結和 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 自動具現化的所有繫結，並將它們連接至檢視中的滑鼠事件。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> 介面包含不同的滑鼠事件的前置處理和後續處理的事件處理常式。 其中一個事件的控點，您可以覆寫的部分中的方法 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>。  
  
###  <a name="editoroperations"></a> 編輯器作業  
 編輯器作業，可以用來自動化編輯器中的，以編寫指令碼或其他用途的互動。 您可以匯入 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 上的存取作業指定 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 您接著可以使用這些物件來修改選取範圍、 捲動檢視，或將插入號移到檢視的不同部分。  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense 支援陳述式完成、 簽章說明 （也稱為 「 參數資訊 」）、 快速諮詢和燈泡。  
  
 陳述式完成提供方法名稱、 XML 項目，與其他程式碼或標記的項目可能完成快顯的清單。 一般情況下，使用者筆勢會叫用完成的工作階段。 工作階段會顯示可能的完整命令清單，使用者可以選取其中一個，或關閉清單。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 是負責建立和觸發 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 計算 <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 的工作階段的完成項目。  
  
## 請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)   
 [編輯器匯入](../extensibility/editor-imports.md)