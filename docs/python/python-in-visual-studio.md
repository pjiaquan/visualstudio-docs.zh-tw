---
title: "Visual Studio 中的 Python | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
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
ms.openlocfilehash: 9f888c27357a5e13fd5e1977bd51a200e928be64
ms.lasthandoff: 03/07/2017

---

# <a name="working-with-python-in-visual-studio"></a>在 Visual Studio 中使用 Python

Python 是一種熱門的程式設計語言，不僅可靠、有彈性、容易學習、可在所有作業系統上免費使用，而且也受到強大的開發人員社群和許多免費程式庫支援。 Python 支援所有形式的開發，包括 Web 應用程式、Web 服務傳統型應用程式、指令碼及科學計算，並且許多大學、科學家、業餘開發人員及專業開發人員等都使用它。 您可以從 [python.org (英文)](https://www.python.org) 和[適用於初學者的 Python (英文)](https://www.python.org/about/gettingstarted/) 深入了解此語言。

Visual Studio 可透過 Python 工作負載 (Visual Studio 2017) 和免費的 Python Tools for Visual Studio 擴充功能 (Visual Studio 2015 和更舊的版本) 為 Python 提供[開放原始碼](https://github.com/Microsoft/ptvs)支援。 

請依照我們的[安裝指示](installation.md)來設定 Python 工作負載，然後使用以下連結來深入了解 Python 相關的功能，以及 Visual Studio 本身的功能。

| 功能 | 描述 | 一般 Visual Studio 文件 | 
| --- | --- | --- |
| [Visual Studio 專案系統](python-projects.md) | 既能夠以隱含方式讀取 Python 程式碼的資料夾結構，又允許採用明確的控制來識別應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等。 | [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md) |
| [專案範本](python-projects.md#project-templates) | 快速建立主控台、Web、Azure、資料科學及其他類型專案的專案結構 | [Visual Studio 範本](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| 多重解譯器支援 | 支援各種版本的 CPython 和 IronPython。 | N/A |
| IPython 支援 | 包含對內嵌繪圖、.NET 及 Windows Presentation Foundation (WPF) 之 REPL 中 IPython/Jupyter 的支援。 | N/A |
| [豐富的編輯、 IntelliSense 及程式碼理解](code-editing.md) | 包含語法色彩標示、所有程式碼和程式庫的自動完成、[程式碼格式設定](code-formatting.md)、簽章說明、類別檢視、移至定義、尋找所有參考、程式碼片段、[重構](code-refactoring.md)、[PyLint](code-pylint.md) 等。 | [在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md) |
| [互動式視窗](interactive-repl.md) | 提供 Python 的快速 REPL 體驗，可讓您輕鬆地醒目提示部分程式碼並將它傳送到 [Interactive Window (互動式視窗)]。 | N/A |
| [功能完整的偵錯](debugging.md) | 可在使用或不使用 Visual Studio 專案的情況下進行偵錯，包括能夠針對現有的可執行檔進行偵錯、進行 [Python/C++ 混合模式偵錯](debugging-mixed-mode.md)、針對 Windows/Linux/Mac 進行[遠端偵錯](debugging-cross-platform-remote.md)、[針對 Azure 進行遠端偵錯](debugging-azure-remote.md)，以及在 [Interactive Window (互動式視窗)] 內進行偵錯。 | [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md) |
| [具備完整報告的分析工具](profiling.md) | 探索您應用程式內時間的使用情況，包括可讓您比較不同分析執行回合間的效能。 | [分析工具](../profiling/profiling-tools.md) (並非所有 Visual Studio 分析功能都可供 Python 使用) |
| [單元測試工具](unit-testing.md) | 在 Visual Studio [測試總管] 中探索、執行及管理測試，並輕鬆針對單元測試進行偵錯。 | [對程式碼進行單元測試](../test/unit-test-your-code.md) |

Python 工作負載也包含 [Azure SDK for Python](azure-sdk-for-python.md)，此 SDK 可將取用端 Azure 服務簡化，並且支援 Windows、Mac OS X 及 Linux。

另請觀賞我們在 YouTube 上的[使用者入門與深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) 系列，這些影片會提供您主要功能的概觀。

[![Python 工具影片](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="features-matrix"></a>功能對照表

您可以下列版本的 Visual Studio 中安裝 Python 支援，如[安裝指南 (英文)](installation.md) 所述：

- [Visual Studio 2017 Preview](https://www.visualstudio.com/vs/preview)
- [Visual Studio 2015 (所有版本)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community 版] (https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)
- [Visual Studio 2013 Express for Web (Update 2 或更新版本)](http://www.microsoft.com/en-us/download/details.aspx?id=40747)
- [Visual Studio 2013 Express for Desktop (Update 2 或更新版本)](http://www.microsoft.com/en-us/download/details.aspx?id=40787)
- Visual Studio 2013 (Pro 版或更新版本)
- Visual Studio 2012 (Pro 版或更新版本)
- Visual Studio 2010 SP1 (Pro 版或更新版本；需要 .NET 4.5)

依 Visual Studio 版本 (Version 和 Edition) 分類的支援功能：

| Python 支援 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 多重解譯器管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動偵測熱門的解譯器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 新增自訂解譯器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 虛擬環境 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip/簡易安裝 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 專案系統 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 來自現有程式碼的新專案 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 顯示所有檔案 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 原始檔控制 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Git 整合 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| 編輯 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 語法醒目提示 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動完成 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 簽章說明 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 快速諮詢 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 物件瀏覽器/類別檢視 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 巡覽列 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 移至定義 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 導覽至 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 尋找所有參考 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動縮排 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 程式碼格式設定 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 重新命名 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 擷取方法 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 新增/移除匯入 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 互動式視窗 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 互動式視窗 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 具有內嵌圖形的 IPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 桌面 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 主控台/Windows 應用程式 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython WPF (含 XAML 設計工具) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython Windows Forms | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Djano Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Bottle Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Flask Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 一般 Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 對網站的 Web 部署 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| 對 Web 角色的 Web 部署 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 對背景工作角色的 Web 部署 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 在 Azure 模擬器中執行 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 遠端偵錯 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| 伺服器總管附加 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Django 範本 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 偵錯 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| CSS 和 JavaScript 的自動完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| 偵錯 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 在不使用檔案的情況下進行偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 偵錯 - 附加至編輯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 混合模式偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 遠端偵錯 (Windows、Mac OS X、Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 偵錯互動式視窗 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 程式碼剖析 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 程式碼剖析 | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| 測試 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 測試總管 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 執行測試 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 偵錯測試 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. [Visual Studio 組件庫](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c)上提供的 Visual Studio Tools for Git 擴充功能中有提供對 VS 2012 的 Git 支援。

2. 部署到「Azure 網站」需要 [Azure SDK for .NET 2.1 - VS 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855)。  較新的版本不支援 VS 2010。

3. 對 Azure「Web 角色」和「背景工作角色」的支援需要 [Azure SDK for .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) 或更新版本。

4. 對 Azure「Web 角色」和「背景工作角色」的支援需要 [Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

5. Visual Studio 2013 中的 Django 範本編輯器有一些已知的問題，這些問題可透過安裝 Update 2 來解決。

6. 需要 Windows 8 或更新版本。 Visual Studio 2013 Express for Web 並沒有 [附加至處理序] 對話方塊，但透過使用 [伺服器總管] 中的 [附加偵錯工具] (Python) 命令，仍然可以進行「Azure 網站」遠端偵錯。 這需要 [Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

7. 需要 Windows 8 或更新版本。 [伺服器總管] 中的 [附加偵錯工具] (Python) 命令需要 [Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

8. 需要 Windows 8 或更新版本。

## <a name="additional-resources"></a>其他資源

- [使用 PyKinect 以 Python 撰寫 Kinect 遊戲 (英文)](https://github.com/Microsoft/PTVS/wiki/PyKinect) (GitHub wiki)
- [IIS 與 Python 之間的 WFastCGI 橋接 (英文)](https://pypi.python.org/pypi/wfastcgi) (python.org)
