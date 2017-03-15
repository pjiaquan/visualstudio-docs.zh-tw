---
title: "逐步解說︰ 顯示燈泡建議 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
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
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>逐步解說︰ 顯示燈泡建議
燈泡是 Visual Studio 編輯器中使用的圖示展開以顯示一組動作，例如修正的內建的程式碼分析器或重構程式碼所識別的問題。  
  
 在 Visual C# 和 Visual Basic 編輯器中，您也可以使用.NET 編譯器平台 ("Roslyn") 來撰寫和封裝您自己的程式碼分析器會自動顯示燈泡的動作。 如需詳細資訊，請參閱:  
  
-   [如何︰ 撰寫 C# 診斷和修正程式碼](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [如何︰ 撰寫 Visual Basic 診斷和修正程式碼](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C + + 等其他語言也提供一些快速的動作，例如建立該函式的虛設常式實作的建議燈泡。  
  
 以下是燈泡的外觀。 在 Visual Basic 或 Visual C# 專案中，紅色曲線會出現在變數名稱無效時。 當滑鼠移過無效的識別項時，燈泡會顯示游標周圍。  
  
 ![燈泡](../extensibility/media/lightbulb.png "燈泡")  
  
 如果您按一下向下箭號的燈泡，一組建議的動作會顯示，以及預覽選取的動作。 在此情況下，它會顯示，如果您執行此動作會對您的程式碼的變更。  
  
 ![燈泡預覽](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 您可以使用燈泡來提供建議的動作。 例如，您可以提供動作，將開啟到下一行的大括號，或將它們移至前一行的結尾。 下列逐步解說示範如何建立在目前的文字會出現燈泡，已有兩種建議的動作︰**轉換為大寫**和**轉換成小寫**。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
1.  建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為`LightBulbTest`。  
  
2.  新增**編輯器分類**項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立副檔名為](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  加入下列參考加入專案，並設定**複製到本機**至`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  加入新的類別檔案，並將它**LightBulbTest**。  
  
6.  新增下列 using 陳述式︰  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>實作燈泡來源提供者  
  
1.  LightBulbTest.cs 類別檔案中刪除 LightBulbTest 類別。 新增名為**TestSuggestedActionsSourceProvider**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> 匯出名稱為**測試建議的動作，**和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的 「 文字 」。</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  內部來源提供者類別中，匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>並將它加入做為屬性。</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>方法來傳回<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>物件。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> 我們將討論在下一節中的來源。  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>實作 ISuggestedActionSource  
 建議的動作來源負責收集組建議的動作，並將它們加入正確的內容中。 在此情況下是目前的文字和建議的動作是**UpperCaseSuggestedAction**和**LowerCaseSuggestedAction**，我們會在下一節中討論。  
  
1.  將類別加入**TestSuggestedActionsSource**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  加入私用的唯讀欄位的建議的動作的來源提供者、 文字緩衝區和文字檢視。  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  新增設定私用欄位的建構函式。  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  加入私用的方法會傳回目前正在進行的資料指標的單字。 下列方法會查看目前游標位置，並要求文字結構導覽文字的範圍。 如果游標位於上一個單字，<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>會以 out 參數傳回，否則`out`參數是`null`且方法會傳回`false`。</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>方法。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 編輯器會呼叫這個方法，以查明是否顯示燈泡。 當進行這個呼叫通常，例如每次您將游標從一行移到另一個，或當滑鼠停留在錯誤波浪線。 這是非同步以便繼續執行時，這個方法使用其他 UI 作業。 因此這個方法只需要執行一些剖析和分析目前的行的大部分的情況下，處理程序可能需要一些時間。  
  
     在我們的實作它以非同步方式取得<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>並判斷是否具有非空白的一些文字範圍是否有意義的亦即。</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>方法，傳回的陣列<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>包含不同的物件<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>物件。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> </xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> 展開燈泡時，會呼叫這個方法。  
  
    > [!WARNING]
    >  您應該先確定實作`HasSuggestedActionsAsync()`和`GetSuggestedActions()`都是一致; 也就是說，如果`HasSuggestedActionsAsync()`傳回`true`，然後`GetSuggestedActions()`應該有一些動作，才能顯示。 在許多情況下`HasSuggestedActionsAsync()`之前呼叫`GetSuggestedActions()`，但是不一定如此。 例如，如果使用者叫用燈泡動作，藉由按下 (CTRL +。) 只`GetSuggestedActions()`呼叫。  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  定義`SuggestedActionsChanged`事件。  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  若要完成實作，新增實作`Dispose()`和`TryGetTelemetryId()`方法。 我們不希望遙測，只要傳回 false，並設定空的 GUID。  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>實作燈泡動作  
  
1.  在專案中，加入至 Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll，並將參考**複製到本機**到`False`。  
  
2.  建立兩個類別，第一個名為`UpperCaseSuggestedAction`和第二個名為`LowerCaseSuggestedAction`。 這兩個類別會實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     這兩個類別是相同的不同之處在於其中一個呼叫<xref:System.String.ToUpper%2A>和其他呼叫<xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A> 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。  
  
3.  新增下列 using 陳述式，這些類別︰  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  宣告一組私用欄位。  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  加入可設定欄位的建構函式。  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>方法，使它顯示動作預覽。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>方法，使它傳回空白<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列舉型別。</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  依照下列所示來實作屬性。  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>方法的範圍中的文字取代成其對等大寫。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  燈泡動作**叫用**方法不會顯示 UI。  如果您的動作會顯示新的使用者介面 （例如預覽或選取範圍 對話方塊），不會顯示直接從 UI **Invoke**方法，但改為排程，以顯示您的 UI 之後從傳回**Invoke**。  
  
10. 若要完成實作，新增`Dispose()`和`TryGetTelemetryId()`方法。  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. 別忘了執行相同的動作，`LowerCaseSuggestedAction`設為 「 轉換 '{0}' 為小寫 」，呼叫<xref:System.String.ToUpper%2A>至<xref:System.String.ToLower%2A>。</xref:System.String.ToLower%2A></xref:System.String.ToUpper%2A>變更顯示文字  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，LightBulbTest 方案中建置並執行它的實驗執行個體。  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔，並輸入一些文字。 您應該會看到燈泡之文字的左邊。  
  
     ![測試燈泡](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  指向燈泡。 您應該會看到向下箭號。  
  
5.  當您按一下燈泡時，兩個建議的動作應該會顯示，以及所選動作的預覽。  
  
     ![測試燈泡，已展開](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  如果您按一下第一個動作，則應該會將目前字組中的所有文字都轉換為大寫。 如果您按一下第二個動作，則應該會將所有文字都轉換為小寫。
