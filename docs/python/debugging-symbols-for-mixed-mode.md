---
title: "混合模式偵錯的符號搭配適用於 Visual Studio 的 Python 工具 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>安裝 Python 解譯器的偵錯符號

為提供完整的偵錯體驗，適用於 Visual Studio 的 Python 工具 (PTVS) 中的[混合模式偵錯工具](debugging-mixed-mode.md)需要剖析正在使用的 Python 解譯器內的許多內部資料結構。 這會需要解譯器本身的偵錯符號。 例如，python27.dll 對應的符號檔為 python27.pdb。

當 PTVS 偵測到它需要符號時，它會提示您指向包含符號檔的資料夾或下載它們︰

![混合模式偵錯期間的符號提示](media/mixed-mode-debugging-symbols-required.png) 

您可以從[官方發行版](#official-distribution) 或[Enthought Canopy](#enthought-canopy) 下載符號檔，如下所述。 如果您使用協力廠商 Python 發行版，例如 ActiveState Python，您將需要連絡該發行版的作者，並要求他們提供符號。 (不過，WinPython 結合了未經變更的標準 Python 解譯器，因此，請使用官方發行版對應版本號碼的符號。)

取得解譯器的 .pdb 檔案後，請依下列步驟執行使 PTVS 知道它們的存在，偵錯工作階段啟動時才會自動載入它們︰

1. 選取 [工具 (Tools)] > [選項 (Options)] 功能表命令，然後瀏覽至 [偵錯 (Debugging)] > [符號 (Symbols)]：

![混合模式偵錯工具符號選項](media/mixed-mode-debugging-symbols.png)

1. 選取工具列上的「新增」按鈕 (上面最左邊的按鈕，! 圖示的右邊)， 瀏覽至包含 .pdb 檔案的資料夾，然後選取 [確定 (OK)]。


## <a name="official-distribution"></a>官方發行版

使用 Python 3.5 和更新版本，您可以透過安裝程式包含偵錯符號 (透過全新安裝或修改現有的安裝)。 選取 [自訂安裝 (Custom installation)]，選取 [下一步 (Next)] 移至 [進階選項 (Advanced Options)]，然後選取 [下載偵錯符號 (Download debugging symbols)]**和 [下載偵錯二進位檔 (Download debug binaries)]** 的方塊：

![包括偵錯符號的 Python 3.x 安裝程式](media/mixed-mode-debugging-symbols-installer35.png)

對於 Python 3.4.x 和更舊版本，符號以可下載的 .zip 檔案提供。 下載之後，將這些檔案解壓縮到某個資料夾，並依照上一節中的指示在 PTVS 中註冊它們。

| Python 版本 | 下載 | 
| --- | --- | 
| 3.4.4 | [32 位元](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 位元](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 位元](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 位元](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 位元](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 位元](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 位元](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 位元](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 位元](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 位元](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 位元](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 位元](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 位元](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 位元](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 位元](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 位元](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 位元](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 位元](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 位元](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 位元](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 位元](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 位元](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 位元](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 位元](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 位元](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 位元](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 位元](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 位元](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 位元](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 位元](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 位元](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 位元](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 位元](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 位元](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 位元](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 位元](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 位元](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 位元](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 位元](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

從 1.2 版開始，Enthought Canopy 提供二進位檔案的符號。 它們會自動隨發行版一起安裝，但是，如先前所述，您仍然需要將包含符號檔的資料夾手動新增至符號路徑。 針對 Canopy 典型的每個使用者安裝，如為 64 位元版本，符號位於 `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts`，如為 32 位元版本，符號位於 `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts`。

Enthought Canopy 1.1 及更舊的版本和 Enthought Python 發行版 (EPD) 不提供解譯器符號，因此不相容於混合模式偵錯。
