---
title: "開始使用 Python | Microsoft Docs"
ms.custom: ""
ms.date: "1/3/2017"
ms.prod: "visual-studio-dev15"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
caps.handback.revision: 10
---
# <a name="getting-started-with-python-in-visual-studio"></a>開始在 Visual Studio 中使用 Python

Python ([http://python.org/download/ (英文)](http://python.org/download/)) 是受歡迎的程式設計語言，它可靠、富彈性、容易學習、免費，而且有強大的開發人員社群和免費程式庫的支援。 Python 可在所有主流作業系統上運作，其用途包含 Web 應用程式、Web 服務、傳統型應用程式、指令碼撰寫，以及科學計算等等。 因此許多大學、科學家、業餘開發人員與專業開發人員都使用它。

若要深入了解此語言，可以從[適用於初學者的 Python (英文)](https://www.python.org/about/gettingstarted/) (python.org) 開始。

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio

適用於 Visual Studio 的 Python 工具 (PTVS)，是免費的開放原始碼 Visual Studio 擴充功能，它提供強大的 Python 開發體驗，包括專案系統和範本、RTF 編輯和 IntelliSense、完整偵錯功能，以及其他各種工具。

擴充功能提供下列功能：

- 支援多個解譯器：CPython、IronPython 及 IPython 的各種版本
- 以隱含方式讀取 Python 程式碼資料夾結構的專案系統，您也可以明確地控制，以便清楚什麼是應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等等的專案系統。
- 適用於主控台、網路、Azure、資料科學，及其他類型的專案。
- 豐富的編輯和程式碼理解功能：語法著色、所有程式碼和程式庫的自動完成、簽章說明、類別檢視、移至定義、尋找所有參考、重構等等。
- 互動 (REPL) 視窗
- 在無 Visual Studio 專案之下進行豐富的偵錯、能夠附加至現有可執行檔、混合模式偵錯、遠端偵錯 Windows/Linux/Mac 和互動式視窗內的偵錯。

- 包含資料視覺效果的 IPython。
- IronPython 和 .NET/WPF 的支援。
- 程式碼剖析工具。
- 測試工具。
- [Azure SDK for Python](#azure-sdk-for-python)

下列資源將協助您開始使用：

- [安裝適用於 Visual Studio 的 Python 工具 (英文)](https://www.visualstudio.com/vs/python/)。
- [安裝指南 (英文)](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- 安裝和功能示範 (27 分鐘) (英文)](https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [文件 (英文)](https://github.com/Microsoft/PTVS/wiki)
- [原始程式碼 (英文)](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python 支援 Windows、Mac 和 Linux，可讓您更容易使用及管理 Microsoft Azure 服務。 詳細資料請參閱下列資源：

- 若要安裝 SDK，請使用 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure)，或遵循 Azure 文件中的[安裝 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/)。
- [Azure SDK for Python 開發人員中心](http://azure.microsoft.com/en-us/develop/python/)中具有從安裝到具有教學課程之文件的大量說明。  一些重點如下：
- 作法指南：
  - [儲存體 Blob](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [儲存體佇列](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [儲存體資料表](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [服務匯流排佇列](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [服務匯流排主題/訂用帳戶](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [服務管理](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- [SDK 的 GitHub 存放庫 (英文)](https://github.com/Azure/azure-sdk-for-python) 的[單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests) 也很適合做為 API 資訊的來源。


## <a name="scientific-computing"></a>科學運算
除了所有 Python 資料科學家程式庫，適用於 Visual Studio 的 Python 工具也支援 IPython 和 IPython Notebooks (可以在 Azure 中裝載)。

建議您從[加州大學爾灣分校 (英文)](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) 取得 IPython 和科學運算程式庫 (Matplotlib、Scipy、Numpy 等等)。

## <a name="see-also"></a>另請參閱
 [PTVS 快速入門：設定 Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [PTVS 快速入門：開始撰寫程式碼 (專案)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [PTVS 快速入門：編輯程式碼](../python/getting-started-with-ptvs-editing-code.md)
 [Getting Started with PTVS: Debugging](../python/getting-started-with-ptvs-debugging.md)
 [PTVS 快速入門：互動式 Python](../python/getting-started-with-ptvs-interactive-python.md)
 [開始使用 PTVS：在 Azure 建置網站](../python/getting-started-with-ptvs-building-a-website-in-azure.md)


<!--HONumber=Feb17_HO4-->


