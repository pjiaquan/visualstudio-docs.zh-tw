---
title: "如何︰ 診斷延伸模組效能 |Microsoft 文件"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
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
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>測量啟動擴充的影響

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>專注於擴充 Visual Studio 2017 效能

根據客戶的意見反應，Visual Studio 2017 發行的焦點區域的其中一個已啟動及方案負載的效能。 當為 Visual Studio 平台小組，我們有已使用的一般改善啟動和方案負載的效能時，我們遙測建議安裝擴充功能也可以在這些案例有相當的影響。

若要協助使用者了解這種影響，我們會通知使用者緩慢的擴充功能的 Visual Studio 中加入的新功能。 當 Visual Studio 偵測到減緩方案載入或啟動的新擴充功能時，使用者會看到 IDE 指向新的 「 管理 Visual Studio 效能 」 對話方塊中的通知。 若要瀏覽先前偵測到的延伸模組的 [說明] 功能表也永遠可以存取此對話方塊。

![管理 Visual Studio 效能](~/docs/extensibility/media/manage-performance.png)

這份文件的目標是為了擴充功能開發人員透過描述擴充功能影響的計算方式，和如何進行分析在本機測試擴充功能可能會顯示為效能，從而影響擴充功能。

## <a name="how-extensions-can-impact-startup"></a>擴充功能可能會如何影響啟動

其中一個延伸模組，對啟動效能影響最常見的方式是藉由選擇要在其中一個已知的啟動 UI 內容，例如 NoSolutionExists 或 ShellInitialized 自動載入。 這些 UI 內容會啟動，並在啟動期間，任何包含 「 ProvideAutoLoad 」 屬性，其定義具有這些內容中的封裝會載入並在該時間初始化。

當我們測量擴充功能的影響時，我們主要著重在選擇要自動載入上述內容中的擴充功能所花費的時間。 測量時間會包含但不是限於︰

* 同步封裝的延伸模組組件的載入
* 同步套件的套件類別建構函式所花費的時間
* 在同步封裝的封裝初始化 （或 SetSite） 方法所花費的時間
* 上述的作業背景執行緒上執行，因此排除在監視非同步封裝
* 在 排程封裝初始化期間，主執行緒上執行任何非同步工作所花費的時間
* 事件處理常式，特別是殼層初始化內容啟動或殼層廢止狀態變更所花費的時間

我們新增了多個從 Visual Studio 2015，協助移除需要封裝自動載入、 延後其負載更特定的情況下，使用者會使用延伸模組，或自動載入時，減少延伸影響更特定的功能。

您可以下列文件中找到更多有關這些功能的詳細資料︰

[規則基礎 UI 內容](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)︰ 建置 UI 內容周圍的豐富以規則為基礎引擎可讓您建立根據專案類型、 類別和功能的自訂內容。 這些自訂內容可以用來更特定的案例，例如專案特定的功能，而不是啟動; 與的目前狀態期間載入的封裝允許或[命令繫結至自訂內容的可見性](https://msdn.microsoft.com/en-us/library/bb166512.aspx)根據專案功能或其他可用的詞彙，而無需載入封裝，以註冊命令狀態查詢處理常式。

[非同步封裝支援](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)︰ 在 Visual Studio 2015 的新 AsyncPackage 基底類別可讓 Visual Studio 封裝為載入背景中以非同步方式時才會自動載入屬性或非同步服務查詢要求載入封裝。 這個背景載入可讓 IDE 擴充功能會在背景中而不會影響重要案例，例如啟動和解決方案的負載持續回應。

[非同步服務](how-to-provide-an-asynchronous-visual-studio-service.md)︰ 非同步封裝的支援，我們也加入支援以非同步方式查詢服務，以及能夠註冊非同步的服務。 更重要的，我們正在轉換至支援非同步查詢，因此大部分的非同步查詢中的工作就會發生在背景執行緒中的核心 Visual Studio 服務。 SComponentModel （Visual Studio MEF 主機） 是一項主要服務現在支援允許延伸模組來支援非同步載入完全非同步查詢。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>減少影響自動載入擴充功能

如果封裝仍然必須自動啟動時載入，務必最小化來降低影響啟動延伸模組的機會封裝初始化期間完成的工作。

可能會導致封裝於較昂貴的初始設定部分範例如下︰

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步封裝負載，而不是非同步的封裝載入

預設會在主執行緒上載入同步的封裝，因為我們鼓勵擁有自動載入封裝，如先前所述的而是使用非同步封裝基底類別的延伸模組擁有者。 變更自動載入的封裝來支援非同步載入也讓您更輕鬆地解決以下的其他問題。

### <a name="synchronous-filenetwork-io-requests"></a>同步的檔案/網路 IO 要求

在理想情況下任何同步的檔案或網路 IO 要求您應該避免使用主執行緒中影響視機器狀態，而且可以封鎖長一段時間，在某些情況下。

使用非同步封裝載入及非同步 IO Api 應該確保封裝初始化不會封鎖主要執行緒在這種情況下，使用者可以繼續在背景中發生的 I/O 要求時，與 Visual Studio 互動。

### <a name="early-initialization-of-services-components"></a>早期的服務元件的初始化

其中一個封裝初始化中的常見模式是初始化或使用該封裝的封裝建構函式或 initialize 方法中所提供的服務。 雖然這可確保服務已準備好用，它也可以將封裝載入未立即使用這些服務時必要的成本。 而這類服務應該初始化依需求降到最低封裝初始化完成的工作。

封裝所提供的全域服務，您可以使用接受函式會由元件在收到要求時，才執行延遲初始化服務的 AddService 方法。 在封裝中使用的服務，您可以利用 Lazy<T>或 AsyncLazy<T>以確保服務的第一次使用初始化/查詢。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>測量影響自動載入使用 PerfView 的擴充功能

雖然程式碼分析可協助您識別可能會降低封裝初始化的程式碼路徑，您也可以使用追蹤使用 PerfView 這類應用程式，了解在 Visual Studio 啟動載入封裝的影響。

PerfView 是系統寬追蹤工具，協助您了解最忙碌路徑可能是因為 CPU 使用量或封鎖系統呼叫的應用程式中。 以下是 快速分析使用 PerfView 網址範例延伸模組範例[Microsoft 下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=28567)。

**範例程式碼︰**

這個範例根據範例以下程式碼，其設計目的是要顯示的情況下延遲部分常見的原因︰

```c#
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**記錄使用 PerfView 追蹤︰**

一旦您安裝 Visual Studio 環境與您安裝的擴充功能，您可以藉由開啟 PerfView，並從 「 收集 」 功能表開啟收集的對話方塊記錄啟動追蹤。

![perfview 收集功能表](~/docs/extensibility/media/perfview-collect-menu.png)

預設選項將會提供 CPU 耗用量的呼叫堆疊，但因為我們是要封鎖的時間，您也應該啟用 「 執行緒的時間 」 堆疊。 設定準備好後您可以按一下 「 開始集合 」，並啟動 Visual Studio，一旦開始錄製。

停止集合之前，您會想要確定 Visual Studio 已完全初始化，主視窗是完全可見，而且如果您的擴充功能，會自動顯示任何 UI 項目，它們也會顯示。 在 Visual Studio 已完全載入，並初始化您的擴充功能，您可以停止分析追蹤記錄。

**分析使用 PerfView 追蹤︰**

完成錄製後 PerfView 會自動開啟追蹤，並展開選項。

基於此範例的目的，我們感主要中的 「 執行緒時間堆疊 」 檢視您可以在 [進階群組] 下找到。 此檢視會顯示方法，包括 CPU 時間和封鎖的時間，例如磁碟 IO，或等候控制代碼的執行緒上所花費的總時間。

 ![執行緒時間堆疊](~/docs/extensibility/media/perfview-thread-time-stacks.png)

 當開啟 「 執行緒時間堆疊 」 檢視，您應該選擇 「 devenv 」 程序來啟動分析。

PerfView 已詳細閱讀執行緒時間堆疊在它自己說明 功能表上，進行更詳細的分析方式的相關指引。 此範例的目的，我們要篩選這個檢視進一步只包括我們封裝的模組名稱和啟動執行緒的堆疊。

1. 「 GroupPats 」 設為空的文字，若要移除任何預設加入的群組。
2. 除了現有的處理程序篩選的集合 」 IncPats 」，包括組件的組件名稱和執行緒啟動。 在此情況下，它應該是 「 devenv;啟動執行緒。MakeVsSlowExtension 」。

現在檢視只會顯示與副檔名相關的組件的相關成本。 在此檢視中，啟動執行緒的"Inc"（內含成本） 資料行底下列出的任何時間是篩選擴充功能和相關影響到啟動。

針對一些有趣的呼叫上述範例會使用堆疊︰

1. IO 使用 System.IO 類別︰ 這些框架內含成本可能非常耗費資源，則表示追蹤中，雖然它們是發生問題的可能原因由於檔案 IO 速度將不同電腦。

  ![系統 io 框架](~/docs/extensibility/media/perfview-system-io-frames.png)

2. 封鎖呼叫等其他非同步工作︰ 在此情況下內含時間代表主執行緒遭到封鎖的非同步工作完成的時間。

  ![封鎖呼叫框架](~/docs/extensibility/media/perfview-blocking-call-frames.png)

其中一個其他檢視中，有助決定影響追蹤將會 「 映像載入堆疊 」。 您可以套用相同的篩選套用至 「 執行緒時間堆疊 」 檢視，並找出您自動載入的封裝所執行的程式碼因為載入所有組件。

請務必載入的組件套件初始化常式內的數目降到最低，每個額外的組件會涉及相當慢的電腦上的啟動速度變慢的額外的磁碟 I/O。

## <a name="summary"></a>總結

啟動 Visual Studio 已我們持續取得回應的區域。 我們稍早所述的目標是要讓所有使用者擁有一致的啟動體驗不論元件和擴充功能安裝軟體，我們想要使用延伸模組的擁有者可以幫助他們協助我們達成這個目標。 上述指引應有助於了解啟動擴充功能影響與可能避免自動載入或載入，以非同步的方式，以減少對使用者產能的影響。
