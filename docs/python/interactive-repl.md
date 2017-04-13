---
title: "Visual Studio 中的 Python 互動式 REPL | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ca444dbe9fea25b205ae2060d462f23957368496
ms.lasthandoff: 04/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>使用 Python 互動式視窗

Visual Studio 為您的每個 Python 環境提供互動式「讀取、求值、輸出」迴圈 (REPL) 視窗，它是以透過命令列上的 `python.exe` 取得的 REPL 為基礎加以改進。 互動式視窗 (透過 [檢視] > [其他視窗] > [&lt;environment&gt; Interactive] 功能表命令開啟) 可讓您輸入任意 Python 程式碼並立即查看結果，這有助於您學習及實驗 API，以及透過互動的方式開發要包含於專案中的程式碼。

![Python 互動式視窗](media/interactive-window.png)

Visual Studio 有多個 Python REPL 模式可供選擇：

| REPL | 描述 | 編輯 | 偵錯 | 影像 |
| --- | --- | --- | --- | --- |
| 標準 | 預設的 REPL，直接與 Python 交談 | 標準編輯 (多行等)。 | 是，透過 `$attach` | 否 |
| 偵錯 | 預設的 REPL，與已完成偵錯的 Python 程序交談 | 標準編輯 | 僅偵錯 | 否 |
| IPython | REPL 與 IPython 後端交談 | IPython 命令、Pylab 便利性 | 否 | 是，內嵌於 REPL |
| IPython (沒有 Pylab) | REPL 與 IPython 後端交談 | 標準 IPython | 否 | 是，獨立視窗 | 

本主題描述「標準」和「偵錯」REPL 模式。 如需 IPython 模式的詳細資料，請參閱[使用 IPython REPL](interactive-repl-ipython.md)。

如需 Python 互動式視窗的簡介，請參閱[開始在 Visual Studio 中使用 Python，第 5 部分：互動式 REPL (英文)](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (youtube.com，2 分 51 秒)。

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>開啟互動式視窗

有多個方式可以開啟環境的互動式視窗。

第一種方式：切換至 [Python 環境] 視窗 ([檢視] > [其他視窗] > [Python 環境] 或 Ctrl-K、Ctrl-`)，並選取所選環境的 [開啟互動式視窗] 命令或按鈕。

![[Python 環境] 視窗中的互動式視窗連結](media/interactive-window-opening.png)

第二種方式：[檢視] > [其他視窗] 具有每個環境的 [互動] 命令，通常顯示在功能表底部：

![[檢視] > [其他視窗] 中的互動式視窗功能表項目](media/interactive-window-menu.png)

第三種方式：您可以選取 [偵錯] > [在 Python Interactive 中執行 [專案 | 檔案]] 功能表命令 (Shift+Alt+F5)，在專案中的啟動檔案上開啟互動式視窗，或是針對獨立檔案開啟互動式視窗：

![在 Python Interactive 功能表中執行專案](media/interactive-execute-project.png)

最後一種方式：您可以選取檔案中的程式碼，並使用於下方描述的[將程式碼傳送至互動式命令](#send-code-to-interactive-command)命令。

## <a name="interactive-window-options"></a>互動式視窗選項

您可以透過 [Python 環境] 視窗中的 [設定互動式視窗]，或透過 [工具] > [選項] > [Python 工具] > [互動式視窗]，來控制互動式視窗的各個部分：

![Python 互動式視窗選項](media/interactive-window-options.png)

請注意，還有一組 [偵錯互動式視窗] 的獨立選項，可控制於偵錯工作階段期間使用時的行為：

![Python 互動式視窗偵錯選項](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>使用互動式視窗

互動式視窗開啟之後，您即可開始在 `>>>` 提示字元逐行輸入程式碼。 隨著您輸入每行程式碼，互動式視窗就會執行它，這包括匯入模組、定義變數等等。 您可以在下圖的前兩行看到此行為：

![Python 互動式視窗](media/interactive-window.png)

當陳述式以冒號做為結尾時則為例外 (如上圖中的 `for` 陳述式)，因為互動式視窗知道它需要其他程式碼行，才能正確執行該程式碼區塊。 在此情況下，行提示字元會變更為 `...`，表示您需要輸入該區塊的其他行，如上圖中的第四和第五行所示。 當您在空白行按下 Enter 時，互動式視窗會關閉該區塊，並在解譯器中執行它。

> [!Tip]
> 互動式視窗是以一般的 Python 命令列 REPL 體驗為基礎加以改進，並會自動對屬於周圍範圍的陳述式做出縮排。 其記錄 (以向上鍵重新叫用) 也會提供多行項目，而命令列 REPL 僅提供單行。

互動式視窗非常適合用來嘗試新的程式庫。 您可以匯入程式庫，檢查子封裝、類別和函式。  Python 可透過其 `help()` 函式告訴您所有資訊。  此外，Visual Studio 中的 Python 支援可提供您以編輯器中使用的程式碼模型為基礎的建議和文件，而不需要執行程式庫。  當您執行程式碼時，Visual Studio 會使用來自 Python 執行階段的資訊來改善這些建議。  

<a name="meta-commands"></a> 互動式視窗也支援數個中繼命令。 所有中繼命令的開頭都是 `$`，而且您可以輸入 `$help` 來取得中繼命令清單，並輸入 `$help <command>` 來取得特定命令的詳細使用方式。

| 中繼命令 | 描述 |
| --- | --- |
| `$$` | 插入註解，這對於在工作階段期間為程式碼做出註解非常有用。 |
| `$attach` | 將 Visual Studio 偵錯工具附加至 REPL 視窗程序以啟用偵錯。 |
| `$cls`, `$clear` | 清除編輯視窗的內容，但不變更記錄和執行內容。 |
| `$help` | 顯示命令清單，或特定命令的說明。 |
| `$load` | 從檔案載入命令並執行，直到完成為止。 |
| `$mod` | 將目前的範圍切換到指定的模組名稱。 |
| `$reset` | 將執行環境重設為初始狀態，但保留記錄。 |
| `$wait` | 至少等候指定的毫秒數。 |

命令也可以透過 MEF (.NET 的 Managed Extensibility Framework) 延伸。

## <a name="switching-scopes"></a>切換範圍

根據預設，專案互動式視窗的範圍是設定為專案的啟動檔案，就如同您從命令提示字元執行它一般。 針對獨立的檔案，則會將範圍設定為該檔案。 不過，您在 REPL 工作階段期間隨時可以從互動式視窗頂端的下拉式功能表變更範圍：

![互動式視窗範圍](media/interactive-scopes.png)

匯入模組之後 (例如輸入 `import os`)，您就會在下拉式清單中看到可切換為該模組中任何範圍的選項。 您也會在互動式視窗中看到表示新範圍的訊息，讓您可以追蹤在工作階段期間抵達某特定狀態的方式。

在範圍中輸入 `dir()` 會顯示該範圍中的有效識別項，包括函數名稱、類別和變數。 例如，使用 `$mod importlib` 並接著使用 `dir()` 會顯示如下內容：

![在 importlib 範圍中的互動式視窗](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>將程式碼傳送至互動式命令

除了直接在互動式視窗內操作之外，您也可以在編輯器中選取程式碼，然後選擇 [傳送到 Interactive]：

![[傳送到 Interactive] 功能表命令](media/interactive-send-to.png)

此功能對於反覆式或演化式程式碼開發非常實用 (包含在開發程式碼時對它進行測試)。 例如，當您將程式碼片段傳送到互動式視窗並查看其輸出之後，您可以按向上鍵以再次顯示該程式碼，修改它，然後按 Ctrl+Enter 來快速測試它。 (在輸入末端按 Enter 鍵將會執行它，但在輸入中間按 Enter 鍵則會插入新的一行)。當您撰寫出所需的程式碼之後，您可以輕鬆地將它複製回您的專案檔案中。

您也可以選取程式碼，以滑鼠右鍵按一下，然後選取 [傳送到定義模組]，系統將會搜尋互動式程序，以尋找符合目前所編輯檔案的模組。 如果命令找到正確的模組，它就會使用 `$mod` 中繼命令來切換至該模組 (而它將會成為互動式視窗工作階段記錄的一部分)，然後將選取的內容貼到互動式視窗以進行評估。 這可以縮短在編輯器中複製程式碼，在互動式視窗中切換範圍，並手動將內容貼上的程序。

## <a name="intellisense-behavior"></a>IntelliSense 行為

互動式視窗包含以即時物件為基礎的 IntelliSense，而不像程式碼編輯器的 IntelliSense，僅以原始程式碼分析為基礎。 這使互動式視窗中的建議更加正確，尤其是針對動態產生的程式碼。 缺點是，具有附加作用 (例如記錄訊息) 的函數可能會影響您的開發體驗。

如果這會造成問題，請在 [工具] > [選項] > [Python 工具] > [互動式視窗] 底下的 [完成模式] 群組中變更設定：

- **一律不評估運算式**：使用一般 IntelliSense 引擎來取得建議。
- **一律不評估包含呼叫的運算式** (預設值)：會評估如 `a.b` 的簡單運算式，但針對 `a().b` 等包含呼叫的運算式，則會使用一般引擎。
- **一律評估運算式**：執行完整的運算式以取得建議，不論它是否具有附加作用。
