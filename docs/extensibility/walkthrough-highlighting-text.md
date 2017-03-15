---
title: "逐步解說︰ 反白顯示文字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>逐步解說︰ 反白顯示文字
您可以建立組件的 Managed Extensibility Framework (MEF) 元件編輯器新增不同的視覺效果。 本逐步解說會示範如何在每次出現的文字檔案中目前的文字反白顯示。 如果字的文字檔案中出現一次以上，您將插入號放一次，每次出現反白顯示。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為`HighlightWordTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[編輯器項目範本以建立副檔名為](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
## <a name="defining-a-textmarkertag"></a>定義 TextMarkerTag  
 反白顯示文字的第一個步驟是子類別化<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>並定義其外觀。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>若要定義 TextMarkerTag 和 MarkerFormatDefinition  
  
1.  將類別檔案，並將它**HighlightWordTag**。  
  
2.  加入下列參考︰  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  匯入下列命名空間。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  建立繼承自類別<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>，並將它`HighlightWordTag`。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  建立第二個類別繼承自<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>，並將它命名為 HighlightWordFormatDefinition。</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 若要使用此格式定義索引標籤，您必須將它匯出具有下列屬性︰  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 標記使用此選項可參考此格式</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 這會導致在 UI 中顯示的格式</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  在 HighlightWordFormatDefinition 的建構函式，定義其顯示名稱和外觀。 Background 屬性定義的填滿色彩、 前景屬性定義的框線色彩。  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  HighlightWordTag 的建構函式，傳入剛才建立的格式定義。  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>實作 ITagger  
 下一步是實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>介面。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 這個介面會指派，以指定的文字緩衝區中，提供文字反白顯示的標記和其他視覺效果。  
  
#### <a name="to-implement-a-tagger"></a>若要實作標註器  
  
1.  建立類別，實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型別的`HighlightWordTag`，並將其命名`HighlightWordTagger`。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  類別中新增下列私用欄位和屬性︰  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>，它會對應至目前的文字檢視。</xref:Microsoft.VisualStudio.Text.Editor.ITextView>  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>，它會對應到文字緩衝區就是文字檢視的基礎。</xref:Microsoft.VisualStudio.Text.ITextBuffer>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>，這用來尋找文字。</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，其具有用於巡覽文字範圍內的方法。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>  
  
    -   A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>，其中包含以反白顯示的字集。</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>，它會對應至目前的文字。</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>，它會對應至目前插入號位置。</xref:Microsoft.VisualStudio.Text.SnapshotPoint>  
  
    -   為鎖定物件。  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  新增的建構函式初始化稍早所列的屬性，並將<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>和<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>事件處理常式。</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  這兩者都會呼叫事件處理常式`UpdateAtCaretPosition`方法。  
  
    ```c#  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  您也必須加入`TagsChanged`將 update 方法呼叫的事件。  
  
     [!code-cs[VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()`方法等同於資料指標所在的位置，建構一份 word 於文字緩衝區中找到的每個字<xref:Microsoft.VisualStudio.Text.SnapshotSpan>物件對應至這個字的出現次數。</xref:Microsoft.VisualStudio.Text.SnapshotSpan> 然後它會呼叫`SynchronousUpdate`，這會引發`TagsChanged`事件。  
  
    ```c#  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate`上執行同步更新`WordSpans`和`CurrentWord`屬性，並引發`TagsChanged`事件。  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  您必須實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法。</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 這個方法會採用一系列<xref:Microsoft.VisualStudio.Text.SnapshotSpan>物件，並傳回標記範圍的列舉。</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
     在 C# 中，實作這個方法與 yield 迭代器，讓延遲的評估 （亦即，將會存取個別的項目時，才評估） 的標記。 在 Visual Basic 中，將標記加入至清單，並傳回清單。  
  
     此方法會傳回<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>物件具有"blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>，它會提供一個藍色背景。</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>建立標註器提供者  
 若要建立您的標註器，您必須實作<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 這個類別是 MEF 元件的組件，因此您必須設定正確的屬性，以便可辨識此延伸模組。  
  
> [!NOTE]
>  如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
#### <a name="to-create-a-tagger-provider"></a>若要建立標註器提供者  
  
1.  建立一個名為`HighlightWordTaggerProvider`實作<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>，並將它匯出與<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「 文字 」 和<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute><xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>的</xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute></xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute></xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  您必須匯入兩個編輯器服務，<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>和<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、 標註器具現化。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  實作<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>方法傳回的執行個體`HighlightWordTagger`。</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，HighlightWordTest 方案中建置並執行它的實驗執行個體。  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>若要建置和測試 HighlightWordTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案，並輸入一些文字中重複出現的文字，例如，"hello hello hello"。  
  
4.  將游標放在一個"hello"的項目。 每個項目應該以藍色反白顯示。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
