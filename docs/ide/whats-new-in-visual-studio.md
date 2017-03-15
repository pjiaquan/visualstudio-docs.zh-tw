---
title: "Visual Studio 2017 RC 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 的新功能
歡迎使用 Visual Studio 2017 RC 這套整合開發人員生產力工具、雲端服務和延伸模組的套件，讓您和您的團隊可以建立適用於網路、Windows 市集、桌上型電腦、Android 及 iOS 的絕佳應用程式和遊戲。  

在我們最新 Visual Studio 版本的這個候選版 (RC) 中，著重在效能和產能的改善。 在效能方面，我們已加快 Visual Studio 的啟動、使其更具回應力，而且使用的記憶體遠少於以前。 在產能方面，我們已新增或更新可讓您在使用 Visual Studio 時更具效率的功能。

> [!TIP]
> 若要查看新的 RC 如何運作，請觀看 Channel 9 上的 [What's New in Visual Studio](https://channel9.msdn.com/events/connect/2016/159) (Visual Studio 的新功能) 影片。   

以下是我們所做變更的高階回顧︰

* **提高產能**。 無論您使用哪種語言或平台，加強程式碼巡覽、IntelliSense、重構、程式碼修正及偵錯，都能節省您花在每日工作的時間和心力。 此外，對於採用 DevOps 的團隊，Visual Studio 2017 則透過即時單元測試和即時架構相依性驗證等全新即時功能，簡化開發人員的內部迴圈，並加速程式碼流程。
* **重新定義基本概念**。  如何提高開發人員每日基礎工作的效率重新受到重視。 從為開發人員需求而量身打造的全新輕量型及模組化安裝，並縮短啟動到關機時間的 IDE，到不需要專案和方案即可檢視程式碼、編輯程式碼並對其偵錯的新方法，Visual Studio 2017 協助開發人員持續關注全貌。
* **簡化 Azure 開發**。 內建 Azure 工具套件讓開發人員能夠輕鬆建立由 Microsoft Azure 提供技術的雲端優先應用程式。 有了 Visual Studio，要直接從 IDE 在 Azure 設定、建置、偵錯、封裝及部署應用程式與服務十分容易。
* **五星級行動裝置開發**。 有了進階偵錯與分析工具以及單元測試產生功能，具有 Xamarin 的 Visual Studio 2017 讓開發人員為 Android、iOS 及 Windows 建置、連接及調整行動裝置應用程式從未如此輕鬆、簡單。 開發人員也可以選擇在 Visual Studio 中使用 Apache Cordova 或 Visual C++ 跨平台程式庫開發，來開發行動裝置應用程式。  

以下是最值得注意的變更的更多詳細資料。

> [!NOTE]
> 如需 Visual Studio 2017 RC 和其後續 RC Refresh 中新功能的完整清單，請參閱[版本資訊](https://www.visualstudio.com/news/vs2015-vs)。 如需問題和因應措施的清單，請參閱版本資訊的 [Known Issues](https://www.visualstudio.com/news/vs2015-vs#knownissues) (已知問題) 小節。   

## <a name="performance-improvements"></a>效能改善

### <a name="a-new-setup-experience"></a>新的安裝經驗  
[Download Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) (下載 Visual Studio Enterprise 2017 RC) 或[Visual Studio 2017 產品系列系統需求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 我們已重新設計 Visual Studio 設定經驗，可更容易在您需要功能時只安裝您所需的功能。 我們也已經減少最少使用量，因此 Visual Studio 的安裝會更為快速，並且對系統的影響也較少。 而且，它也會完全進行解除安裝。

 您會在安裝 Visual Studio 時看到的最重要變更是其新的安裝體驗。 在 [工作負載] 索引標籤上，您會看到群組在一起的安裝選項來代表通用架構、語言及平台，範圍涵蓋從 .NET 桌面開發到採用 R、Python 和 F# 的資料科學。  

 ![Visual Studio 2017 RC 安裝程式對話方塊](../ide/media/willow1.png "安裝 Visual Studio 2017")

選擇您需要的工作負載，並在需要時進行變更。 最小安裝的大小雖然只有幾百 MB，但仍包含基本程式碼編輯支援，可支援&20; 種以上的語言與原始程式碼控制功能。

我們也新增不同的方法來安裝 Visual Studio。 想要選擇您自己的元件，而不是使用工作負載嗎？ 只需從安裝程式選取 [個別元件] 索引標籤。 想要安裝語言套件，同時不需要變更 Windows 語言選項嗎？ 選擇安裝程式的 [語言套件] 索引標籤。  

若要更深入了解新的安裝體驗 (包括引導您執行這項作業的逐步指示)，請參閱[安裝 Visual Studio](../install/install-visual-studio.md) 頁面。


### <a name="start-visual-studio-faster"></a>更快速啟動 Visual Studio
如果 Visual Studio 偵測到 IDE 啟動時間變慢，則會提供新的 Visual Studio 效能中心來協助您加快速度。 效能中心會列出所有讓 IDE 啟動變慢的延伸模組和工具視窗。 您可以使用它來改善啟動效能，方法是判斷延伸模組啟動時機，或是否在啟動時開啟工具視窗。

### <a name="decrease-solution-load-time"></a>減少解決方案載入時間
處理包含多達 100 個專案的方案，並不表示您需要一次處理所有檔案或專案。 您現在可以進行編輯和偵錯，而不需要等待 Visual Studio 載入每個專案。 若要使用 Managed 專案進行試用，請從 [工具] -> [選項] -> [專案和方案] 中開啟 [輕量型解決方案載入]。

  ![Visual Studio 2017 RC 中的 [選項] 對話方塊](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "VS2017RC [選項] 對話方塊 - 輕量型解決方案載入")

### <a name="faster-on-demand-loading-of-extensions"></a>依需求更快速地載入延伸模組
這個概念十分簡單︰在需要時載入延伸模組，而不是 Visual Studio 啟動時。 首先，我們將 Python 和 Xamarin 延伸模組轉換成在需要時載入，接下來，致力於將 Visual Studio 隨附的所有延伸模組以及協力廠商隨附的延伸模組移至此模型。 想要知道哪些延伸模組影響啟動、解決方案載入和輸入效能嗎？ 您可以在 [說明] -> [管理 Visual Studio 效能] 中查看這項資訊。

  ![Visual Studio 2017 RC 中的 [選項] 對話方塊](../ide/media/vs2017ide-ManageVSperf.png "VS2017RC [說明] 對話方塊 - 效能管理")

## <a name="productivity-improvements"></a>產能提升

### <a name="sign-in-across-multiple-accounts"></a>跨多個帳戶登入  
我們已在 Visual Studio 2017 RC 中引進新的身分識別服務，可讓您在 Microsoft 開發人員工具之間共用使用者帳戶，例如 Team Explorer、Azure Tools、Windows 市集發行和其他工具。

另外，您可以登入更長的時間；我們不會要求您每 12 小時重新登入一次。 若要深入了解，請參閱 [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (較少的 Visual Studio 登入提示) 部落格文章。

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>使用漫遊延伸模組管理員來管理延伸模組
現在，登入 Visual Studio 時，可以更容易地使用慣用延伸模組來設定每個開發環境。 新的漫遊延伸模組管理員會在雲端中建立一份同步清單，以追蹤您的所有慣用延伸模組。  

若要查看 Visual Studio 中的延伸模組清單，請按一下 [工具] > [延伸模組和更新]，然後按一下 [漫遊延伸模組管理員]。

![Visual Studio 2017 - [延伸模組和更新] 對話方塊](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 - [工具] > [延伸模組和更新] 對話方塊")

漫遊延伸模組管理員會追蹤您安裝的所有延伸模組，但是您可以選擇想要新增至 [漫遊] 清單的延伸模組。

![Visual Studio 2017 - [延伸模組和更新] 對話方塊](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - 漫遊延伸模組管理員")

當您使用漫遊延伸模組管理員時，會在清單中看到 3 個圖示類型︰
* ![Roamed (已漫遊) 圖示](../ide/media/vs2017ide-roamedicon.png "Roamed (已漫遊) 圖示") *** Roamed (已漫遊) 圖示***︰延伸模組已在此 [漫遊] 清單中，但尚未安裝在電腦上
  (您可以使用 [下載] 按鈕進行安裝)。
* ![Roamed and Installed (已漫遊並已安裝) 圖示](../ide/media/vs2017ide-roamedinstalledicon.png "Roamed and Installed (已漫遊並已安裝) 圖示") ***Roamed and Installed (已漫遊並已安裝) 圖示***︰所有延伸模組都在此 [漫遊] 清單中，並已安裝在開發環境中
  (如果您決定不再漫遊，則可以使用 [停止漫遊] 按鈕予以移除)。
* ![Installed (已安裝) 圖示](../ide/media/vs2017ide-installedicon.png "Installed (已安裝) 圖示") ***Installed (已安裝) 圖示***︰所有延伸模組都已安裝在此環境中，但不在 [漫遊] 清單中
  (使用 [開始漫遊] 按鈕，即可將延伸模組新增至 [漫遊] 清單)。

這些圖示會顯示您清單的目前狀態。 您可依據需要，自訂任何狀態的任何擴充功能， 也可以由我們為您代勞！ 您在登入後下載的任何延伸模組都會新增至您的清單並顯示為 [Roamed and Installed] (已漫遊並已安裝)，而且出現在 [漫遊] 清單中，讓您可以從任何電腦存取延伸模組！

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>體驗即時架構相依性驗證和即時單元測試

在 Visual Studio Enterprise 2017 RC 中，如果您已設定相依性驗證圖表 (也稱為 分層圖)，則現在於程式碼編輯器中輸入程式碼時，會即時通知您發生架構相依性規則違規。

錯誤會出現在 [錯誤清單] 中，而且文字編輯器中的波浪線會顯示違規的確切位置。 您現在較不容易引進不想要的相依性。

![即時驗證架構](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "即時驗證架構相依性")

#### <a name="live-unit-testing"></a>即時單元測試：

即時單元測試是我們引進的新功能，且僅出現在 Visual Studio Enterprise 版中。 這項功能會在您撰寫程式碼時，在編輯器中即時以視覺化方式呈現單元測試結果和程式碼涵蓋範圍。 它可與 .NET Framework 的 C#/VB 專案搭配使用，並支援 MSTest、xUnit 及 NUnit 三種測試架構。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 加強功能
#### <a name="interact-with-git"></a>與 Git 互動：
Visual Studio IDE 下方中的控制項可讓您快速認可並將專案發行至 Git，以及管理 Git 存放庫。

![Visual Studio 2017 RC 安裝程式對話方塊](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>使用結構視覺化檢視來檢視和巡覽程式碼︰
Visual Studio 程式碼編輯器中具有稱為「結構視覺化檢視」的新功能。 這項功能會在巢狀程式碼區域之間顯示垂直輔助線，讓您更輕鬆地檢視和巡覽程式碼。 這項功能適用於所有 TextMate 支援的語言，以及 Visual C#、Visual Basic 和 XAML。

![Visual Studio 2017 RC 安裝程式對話方塊](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>遇到改善的 [巡覽至]︰
我們已改善 [巡覽至] 函式。 我們已簡化 [巡覽至] 視窗，並且已新增可讓您縮小程式碼搜尋範圍的額外篩選字元支援。

#### <a name="create-apps-in-even-more-programming-languages"></a>甚至以更多的程式設計語言來建立應用程式︰
您可以使用比舊版還要多的程式設計語言在 Visual Studio 中建立應用程式，因此不再需要方案和專案。 您的程式碼會取得語法顏色標示、基本陳述式完成，有時還會取得 [巡覽至] 和其他支援。 如果您偏好的語言不予支援，則可以使用 TextMate 文法來建立其支援。

### <a name="visual-c"></a>Visual C++
Visual Studio 2017 RC 帶來多項 Visual C++ 環境的更新與修正。 我們修正了編譯器及工具中超過 250 個 Bug 與回報的問題，其中多為客戶透過 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 所提交。

我們也進行數項改進，包括散發 Visual Studio 的 C++ 核心指南、新增增強的 C++11 和 C++ 功能支援以更新編譯器、新增和更新 C++ 程式庫中的功能，以及提升 C++ IDE、安裝工作負載和其他項目的效能。

如需完整詳細資訊，請參閱 [Visual 2017 RC 中的 Visual C++ 新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)頁面。  


### <a name="debugging-and-diagnostics"></a>偵錯和診斷
偵錯的速度現在更快，而且不會在編輯時導致延遲。

例如︰在舊版 Visual Studio 中，我們針對 WPF、Windows Forms 和 Managed 主控台專案引進裝載處理序以更快速進行偵錯，方法是在背景中啟動處理序以用於下一個偵錯工作階段。 當您在偵錯工作階段結束後停止偵錯或使用 Visual Studio 時，這個用意良好的功能導致 Visual Studio 暫時無法回應數秒。

在 Visual Studio 2017 中，我們已關閉裝載處理序，並最佳化偵錯，就像沒有裝載處理序一樣快，而從未使用裝載處理序的專案甚至會更快 (例如 ASP.NET、Universal Windows 和 C++ 專案)。

#### <a name="run-to-click"></a>執行至點選處：
現在，進行偵錯時，可以按一下程式碼行旁的圖示來執行該行。 您不再需要設定暫時中斷點來執行多項步驟，就能執行程式碼並停在想要的程式行。

![Visual Studio 2017 RC 偵錯 - 執行至點選處](../ide/media/vs2017ide-RunToClick.png "Visual Studio 2017 偵錯和診斷中的 [執行至點選處]")

#### <a name="the-new-exception-helper"></a>新的例外狀況協助程式：

您可以使用新的例外狀況協助程式立即存取內部例外狀況，快速檢視壓縮的非強制回應對話方塊中的例外狀況資訊。

診斷 NullReferenceException 時，可快速在例外狀況協助程式中查看哪些項目為 Null。

您也可以排除從特定模組擲回例外狀況類型所造成的中斷，方法是按一下核取方塊，以新增在擲回例外狀況時停止的條件。

![[新增例外狀況協助程式] 對話方塊](../ide/media/vs2017ide-ExceptionHelper.png "[新增例外狀況協助程式] 對話方塊")

如需詳細資訊，請參閱 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

## <a name="talk-to-us"></a>告訴我們  
 為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應。 它們是我們進步的動力。  

如果您想要建議我們如何改善 Visual Studio，或回報問題，請參閱[告訴我們](../ide/talk-to-us.md)頁面來取得詳細資訊。  

### <a name="report-a-problem"></a>回報問題  
 訊息有時無法完整傳達您所發生問題的完整影響。 如果您遇到停止回應、當機或其他效能問題，則可以使用 [回報問題] 工具，輕鬆地與我們分享重現步驟和支援檔案 (例如螢幕擷取畫面以及追蹤和堆積傾印檔案)。 如需如何使用此工具的詳細資訊，請參閱[如何回報問題](how-to-report-a-problem-with-visual-studio-2017.md)頁面。  

### <a name="track-your-issue-in-connect"></a>使用 Connect 追蹤您的問題  
 如果您想要追蹤 Visual Studio 意見反應的狀態，只需要前往 [Connect](http://connect.microsoft.com/) 並回報 Bug。 回報 Bug 之後，就可以回到 Connect 來追蹤其狀態。  

## <a name="see-also"></a>另請參閱  
* [Visual C++ 的新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# 的新功能](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Team Foundation Server 的新功能](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio 版本資訊](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


