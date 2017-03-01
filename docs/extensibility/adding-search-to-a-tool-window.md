---
title: "工具視窗加入搜尋 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
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
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>加入搜尋工具視窗
當您建立或更新您的擴充功能中的工具視窗時，您可以在 Visual Studio 中加入相同的搜尋功能，會出現在其他地方。 這些功能包括下列功能︰  
  
-   一定會位於工具列的自訂區域中 [搜尋] 方塊中。  
  
-   進度指示器，以顯示在 [搜尋] 方塊本身。  
  
-   一旦您輸入每個字元 （即時搜尋），或選擇 Enter 鍵 （視搜尋） 之後，才會顯示結果的能力。  
  
-   顯示供您搜尋過最新的詞彙清單。  
  
-   篩選搜尋特定欄位或搜尋目標方面的功能。  
  
 按照本逐步解說，您將了解如何執行下列工作︰  
  
1.  建立 VSPackage 專案。  
  
2.  建立工具視窗，其中包含與唯讀文字方塊 UserControl。  
  
3.  將搜尋方塊加入至 [工具] 視窗。  
  
4.  加入搜尋實作。  
  
5.  啟用即時搜尋和顯示進度列。  
  
6.  新增**大小寫須相符**選項。  
  
7.  新增**搜尋只偶數行**篩選器。  
  
## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案  
  
1.  建立 VSIX 專案，名為`TestToolWindowSearch`與名為工具視窗**TestSearch**。 如果您需要執行此動作的說明，請參閱[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="to-create-a-tool-window"></a>建立工具視窗  
  
1.  在`TestToolWindowSearch`專案中開啟 TestSearchControl.xaml 檔案。  
  
2.  取代現有`<StackPanel>`區塊中以下列的區塊中，加入唯讀<xref:System.Windows.Controls.TextBox>至<xref:System.Windows.Controls.UserControl>工具視窗中。</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  在 TestSearchControl.xaml.cs 檔案中，新增下列 using 陳述式︰  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  移除`button1_Click()`方法。  
  
     在**TestSearchControl**類別中，新增下列程式碼。  
  
     這個程式碼加入公用<xref:System.Windows.Controls.TextBox>屬性名為**SearchResultsTextBox**和公用字串屬性，名為**SearchContent**。</xref:System.Windows.Controls.TextBox> 在建構函式，SearchResultsTextBox 設為 [文字] 方塊中，而且 SearchContent 會初始化為新行字元分隔的字串。 文字方塊的內容也會初始化為字串集合中。  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[ToolWindowSearch&#1;](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch&#1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
6.  在功能表列上選擇 **檢視**，**其他視窗**， **TestSearch**。  
  
     工具視窗隨即出現，但不會顯示搜尋控制項。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>將搜尋方塊新增至 [工具] 視窗  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼`TestSearch`類別。 程式碼會覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性，使傳回的 get 存取子`true`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     若要啟用搜尋，您必須覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>，並提供不會啟用搜尋的預設實作。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
3.  在 Visual Studio 的實驗執行個體，開啟**TestSearch**。  
  
     在 [工具] 視窗頂端，搜尋都會出現一個控制項與**搜尋**浮水印及放大玻璃圖示。 不過，不會使用搜尋尚未因為目前尚未提供搜尋程序。  
  
## <a name="to-add-the-search-implementation"></a>若要加入搜尋  
 當您啟用搜尋上<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>，如先前的程序，在 [工具] 視窗中建立搜尋主機。</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 此主機設定，及管理搜尋處理序，一律在背景執行緒進行。 因為<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別會建立搜尋主機及設定管理向上搜尋的您只需要建立搜尋工作，並提供搜尋方法。</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 搜尋程序就會發生在背景執行緒，並在 UI 執行緒上發生的工具視窗控制項的呼叫。 因此，您必須使用<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>來管理您在處理控制項的任何呼叫的方法。</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  在 TestSearch.cs 檔案中，新增下列`using`陳述式︰  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  在`TestSearch`類別中，新增下列程式碼，執行下列動作︰  
  
    -   覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>方法來建立搜尋工作。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>方法以還原的文字方塊中的狀態。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 當使用者取消搜尋工作，以及當使用者設定或取消設定選項或篩選條件時，會呼叫這個方法。 同時<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI 執行緒上呼叫。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 因此，您不需要存取文字方塊中，藉由<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法。</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   建立類別，名為`TestSearchTask`繼承自<xref:Microsoft.VisualStudio.Shell.VsSearchTask>提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>的預設實作，</xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         在`TestSearchTask`，建構函式設定參照 [工具] 視窗中的私用欄位。 若要提供的搜尋方法，您覆寫<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法是您用來實作搜尋程序。</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 此程序包括執行搜尋、 顯示在文字方塊中，搜尋結果，並呼叫基底類別實作，這個方法來搜尋已完成的報表。  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  測試您的搜尋實作執行下列步驟︰  
  
    1.  重建專案並開始偵錯。  
  
    2.  在 Visual Studio 的實驗執行個體，一次開啟 [工具] 視窗，在 [搜尋] 視窗中，輸入搜尋文字，並按一下 ENTER。  
  
         正確的結果應該會出現。  
  
## <a name="to-customize-the-search-behavior"></a>若要自訂搜尋行為  
 藉由變更搜尋設定，可以在搜尋控制項的顯示方式，以及執行搜尋時如何進行各種變更。 例如，您可以變更浮水印 （預設值的文字出現在 [搜尋] 方塊中）、 最小值和最大寬度的搜尋控制項，以及是否要顯示進度列。 您也可以變更的點開始 （隨選或立即搜尋） 上會顯示搜尋結果，以及是否要顯示供您最近的搜尋的字詞的清單。 您可以在<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>類別</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>中找到設定的完整清單  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼`TestSearch`類別。 此程式碼可讓您立即搜尋，而不是隨搜尋 （表示使用者不需要按 enter 鍵）。 程式碼會覆寫`ProvideSearchSettings`方法中的`TestSearch`類別，需要變更預設設定。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  測試新設定重新建置方案，然後重新啟動偵錯工具。  
  
     搜尋結果會顯示每次您在 [搜尋] 方塊中輸入字元。  
  
3.  在`ProvideSearchSettings`方法中，新增下列命令，可顯示進度列。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     顯示進度列，必須報告進度。 若要報告進度，取消註解下列程式碼中的`OnStartSearch`方法`TestSearchTask`類別︰  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  若要減緩處理足夠的進度列是可見的取消註解中的這行`OnStartSearch`方法`TestSearchTask`類別︰  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  重建方案，然後啟動 debugb 來測試新的設定。  
  
     進度列會出現在 [搜尋] 視窗 （做為搜尋文字方塊下方的藍色列） 每次您執行搜尋。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>若要讓使用者以精簡搜尋結果  
 您可以允許使用者透過選項精簡其搜尋，例如**大小寫須相符**或**字拼寫須相符**。 選項可以是布林值，其中會顯示為核取方塊或顯示為按鈕的命令。 此逐步解說中，您將建立布林值的選項。  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼`TestSearch`類別。 程式碼會覆寫`SearchOptionsEnum`方法，可以讓搜尋實作偵測指定的選項是開啟或關閉。 中的程式碼`SearchOptionsEnum`新增選項，以便符合大小寫，以<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列舉值。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 大小寫須相符的選項也都可以提供為`MatchCaseOption`屬性。  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  在`TestSearchTask`類別中，取消註解中的 matchCase 行`OnStartSearch`方法︰  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  測試選項︰  
  
    1.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
    2.  在 [工具] 視窗中，選擇 [文字] 方塊右邊的向下箭頭。  
  
         **大小寫須相符**出現核取方塊。  
  
    3.  選取**大小寫須相符**核取方塊，然後再執行 某些搜尋。  
  
## <a name="to-add-a-search-filter"></a>若要加入搜尋篩選  
 您可以加入搜尋篩選器，讓使用者以精簡搜尋目標集。 比方說，您可以依它們所修改之最新的日期和其檔案名稱的副檔名篩選檔案總管 中的檔案。 在本逐步解說中，您將新增只偶數行的篩選。 當使用者選擇該篩選條件時，搜尋主機會將您所指定的字串將搜尋查詢。 您可以識別您的搜尋方法內的這些字串，並據以篩選的搜尋目標。  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼`TestSearch`類別。 程式碼實作`SearchFiltersEnum`加<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>可指定要篩選搜尋結果，如此只有甚至行就會顯示。</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     現在搜尋控制項中顯示搜尋篩選`Search even lines only`。 當使用者選擇篩選器，並將字串`lines:"even"`會出現在 [搜尋] 方塊。 其他搜尋條件可以出現在相同的時間為篩選條件。 搜尋字串可能之前篩選，篩選器，或兩者之後會出現。  
  
2.  在 TestSearch.cs 檔案中新增下列方法來`TestSearchTask`類別，這是在`TestSearch`類別。 這些方法支援`OnStartSearch`方法，您將在下一個步驟中修改。  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  在`TestSearchTask`類別中，更新`OnStartSearch`為下列程式碼的方法。 這項變更會更新以支援篩選器的程式碼。  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  測試您的程式碼。  
  
5.  建置此專案並開始偵錯。 在 Visual Studio 的實驗執行個體，開啟 [工具] 視窗，然後選擇搜尋控制項上的向下箭頭。  
  
     **大小寫須相符**核取方塊和**搜尋只偶數行**篩選會出現。  
  
6.  選擇篩選器。  
  
     [搜尋] 方塊包含**幾行︰ 偶數 」**，並會出現下列結果︰  
  
     良好的&2;  
  
     4 良好  
  
     6 再見  
  
7.  刪除`lines:"even"`從 [搜尋] 方塊中，選取**大小寫須相符**核取方塊，然後再輸入`g`在搜尋方塊中。  
  
     此時會出現下列結果︰  
  
     1 到  
  
     良好的&2;  
  
     5 再見  
  
8.  選擇 [搜尋] 方塊右邊的 X。  
  
     清除搜尋，並顯示原始內容。 不過，**大小寫須相符**仍選取核取方塊。
