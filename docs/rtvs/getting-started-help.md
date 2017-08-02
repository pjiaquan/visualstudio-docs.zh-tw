---
title: "Visual Studio R 工具中的 [說明] 視窗 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
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
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio R 工具中的說明

R 說明已直接整合至 Visual Studio 的互動式視窗。 每當您使用 `?` 命令，例如 `?mtcars` 時，R 文件中的說明會出現在 Visual Studio 視窗︰

![Visual Studio 的 [說明] 視窗](~/rtvs/media/help-window.png)

> [!Tip]
> [說明] 視窗就像 Visual Studio 的所有其他視窗，可以讓您隨心所欲地排列和停駐。 請參閱[在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。
>
> 您也可以在瀏覽器中開啟說明結果，而不是選取 [R 工具] > [選項] 功能表，並將 **R 說明瀏覽器**屬性設為 `External`。 請參閱[選項](options.md)。

若要搜尋說明，請使用 `??` 命令並以引號括住搜尋字詞 (如果它包含空格)︰

```R
??"Motor Trend"
```

![說明搜尋結果](~/rtvs/media/help-search1.png)

[說明] 視窗也有搜尋輸入欄位，讓您可以直接在 R 文件中執行進一步搜尋︰

![使用輸入欄位的說明搜尋結果](~/rtvs/media/help-search2.png)

## <a name="integrated-help-lookup"></a>整合式說明查閱

因為開發人員經常會在 R 文件搜尋函式名稱、資料集和其他項目的說明，所以 Visual Studio R 工具藉由將說明查閱直接整合到編輯器和互動式視窗，以簡化程序。

- 在自動完成的作業期間按 F1 鍵，會產生符合子字串的說明結果清單。
- 以滑鼠右鍵按一下搜尋字詞 (例如函式)，然後選取 [說明於] 命令，或是只按 F1 鍵，即可開啟該函式的說明。 您也可以對任何選取範圍叫用 [說明於]。

    ![透過以滑鼠右鍵按一下的操作功能表叫用說明](~/rtvs/media/help-right-click.png)

> [!Tip]
> 若要在瀏覽器中開啟整合式說明，請選取 [R 工具] > [選項]，並將 [F1 網頁瀏覽器] 設定為 `External`。 請參閱[選項](options.md)。

## <a name="integrated-stackoverflow-search"></a>整合式 StackOverflow 搜尋

除了在 R 文件中搜尋之外，開發人員也經常在撰寫程式碼時搜尋 StackOverflow。 RTVS 也可以簡化這個程序。 當您以滑鼠右鍵按一下字詞或選取範圍，並選取 [在網路上搜尋] 命令時，或是只按 Ctrl + F1，會開啟一個 Visual Studio 視窗 (或瀏覽器，如果您已經變更 [F1 網頁瀏覽器] 選項的話)，其中包含範圍預設為 StackOverflow 的該字詞搜尋結果︰

![Visual Studio 中的網路搜尋結果](~/rtvs/media/help-web-search-results.png)

您可以變更附加的字串 `R site:stackoverflow`，透過 [R 工具] > [選項] > [F1 網路搜尋字串] 選項︰

![變更 F1 網路搜尋字串選項](~/rtvs/media/options-dialog.png)
