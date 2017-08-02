---
title: "使用 Visual Studio 中的 PyLint | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
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
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>使用 PyLint 檢查 Python 程式碼

[PyLint](https://www.pylint.org/) 是一種廣泛使用的工具，可檢查 Python 程式碼中的錯誤，有助於撰寫良好的 Python 程式碼模式，因此 Visual Studio 已針對 Python 專案整合這項工具。

只要在 [方案總管] 中以滑鼠右鍵按一下 Python 專案，並選取 [Python] > [執行 PyLint]：

![操作功能表上 Python 專案的 PyLint 命令](~/python/media/code-pylint-command.png)

如有需要，使用命令提示字元將 PyLint 安裝到您的使用中環境。

PyLint 警告和錯誤會出現在 [錯誤清單] 視窗中︰

![PyLint 錯誤清單](~/python/media/code-pylint-error-list.png)

按兩下錯誤會帶您直接前往產生問題的原始程式碼。

> [!Tip]
> 如需所有 PyLint 輸出訊息的詳細清單，請參閱 [PyLint 功能參考 (英文)](https://pylint.readthedocs.io/en/latest/reference_guide/features.html)。

## <a name="setting-pylint-command-line-options"></a>設定 PyLint 命令列選項

PyLint 文件的[命令列選項 (英文)](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) 一節描述如何透過 `.pylintrc` 組態檔控制 PyLint 的行為。 這類檔案可以放在 Visual Studio Python 專案的根目錄中或其他位置 (視您想要將這些設定套用的範圍而定)。

例如，若要在專案的 `.pylintrc` 檔案中隱藏上一個影像中顯示的「遺失 docstring ("missing docstring")」的警告，請執行下列動作︰

1. 在命令列中，瀏覽至您的專案根目錄 (您可以在其中找到您的 `.pyproj` 檔案)，然後執行下列命令來產生已加註解的組態檔︰

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. 在 Visual Studio [方案總管] 中，以滑鼠右鍵按一下您的專案，選取 [加入] > [結束項目...]，瀏覽並選取新的 `.pylintrc` 檔案，然後選取 [加入]。

1. 開啟要編輯的檔案，您會看到各種可以使用的設定。 若要停用警告，請找出 `[MESSAGES CONTROL]` 區段，然後找出該區段下方的 `disable` 設定。 您會看到一長串的特定訊息，您可以在其中附加您想要的任何警告。 在此範例中，請附加 `,missing-docstring` (包括其中的逗號)。

1. 儲存 `.pylintrc` 檔案，重新執行 PyLint，您會發現警告現在已經隱藏。
