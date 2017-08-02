---
title: "使用 Visual Studio R 工具進行偵錯 | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>在 Visual Studio 中對 R 進行偵錯

Visual Studio R 工具 (RTVS) 與完整的 Visual Studio 偵錯體驗整合 (請參閱 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md))，包括中斷點、附加至執行中處理序、檢查和監看變數、檢查呼叫堆疊等等。 本主題會瀏覽 R 和 RTVS 特有的偵錯觀點。

在 R 專案中，啟動 R 檔案的偵錯工具啟動方式，與其他專案類型一樣︰使用 [偵錯] > [啟動偵錯]、F5 鍵，或 [偵錯] 工具列上的 [執行啟動檔案]，如下所示。 若要變更啟動檔案，請在方案總管中以滑鼠右鍵按一下檔案，然後選取 [設定為啟動 R 指令碼]。

![R 的偵錯工具 [開始] 按鈕](~/rtvs/media/debugger-start-button.png)

在所有情況下，啟動偵錯工具會在互動式視窗中「執行」檔案，這表示載入它並在那裡執行該檔案。 事實上，當您開始偵錯時，您會在互動式視窗中看到如下的輸出︰

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

您會注意到，我們使用 `rtvs::debug_source` 函式來執行指令碼。 這是必要的，因為 RTVS 需要修改您的程式碼，以準備進行偵錯。 如果您使用任何 RTVS 命令 (例如，在方案總管中以滑鼠右鍵按一下檔案，並執行 [所選來源檔案] 命令)，並且已附加偵錯工具，我們會把呼叫自動重新導向至 `rtvs::debug_source`。

您也可以手動從互動式視窗中直接使用 [R 工具] > [工作階段] > [附加偵錯工具] 命令、[偵錯] > [附加至 R 互動] 命令，或互動式視窗工具列上的 [附加偵錯工具] 命令，來附加偵錯工具。 一旦您這麼做，您便必須負責執行您要偵錯的檔案。 如果您想要手動執行檔案，請確定您使用 `rtvs::debug_source` 而不是 R 中的一般 `source` 命令。您可能會發現，這適用於「一些」情況，但我們無法保證在所有情況下偵錯都可運作，除非您使用 `rtvs::debug_source` 命令。

偵錯工具和互動式視窗之間的這項連接使您能夠更輕鬆地進行作業，例如使用不同的參數值來呼叫 (和偵錯) 函式。 例如，假設您在執行的檔案 (亦即它已載入至工作階段) 中有如下的函式︰

```R
add <- function(x, y) {
    return(x + y)
}
```

那麼您要在 `return` 陳述式上設定中斷點。 現在，在互動式視窗中，如果您輸入 `add(4,5)`，您會看到偵錯工具在中斷點上停止。


## <a name="environment-browser-in-the-interactive-window"></a>互動式視窗中的環境瀏覽器

當您在偵錯工具中停止時，您也會在[互動式視窗](interactive-repl.md)中的環境瀏覽器提示字元停止。 提示會顯示為 `Browse[n]>`，其中 n 為數字。

環境瀏覽器支援許多特殊命令︰

| 命令 | 說明 | 
| --- | --- |
| n | 下一步︰執行程式碼檔案中的下一個陳述式 (與不進入函式相同)。 |
| s | 逐步執行︰執行程式碼檔案中的下一個陳述式，如果下一個陳述式是函式呼叫，則逐步執行函式範圍。 | 
| f | 完成︰執行目前函式範圍的其餘部分，並傳回給呼叫端 (與跳離函式相同)。 |
| c、cont | 繼續︰執行程式直到下一個中斷點。 | 
| Q | 結束：結束偵錯工作階段。 |
| 其中 | 顯示堆疊︰在互動式視窗中顯示呼叫堆疊。 |
| help | 顯示說明︰在互動式視窗中顯示可用的命令。 |
| &lt;expr&gt; | 評估 *expr* 中的運算式。 |

![互動式視窗中的環境瀏覽器](~/rtvs/media/debugger-environment-browser.png)

