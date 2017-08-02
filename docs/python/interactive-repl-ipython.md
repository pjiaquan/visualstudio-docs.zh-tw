---
title: "Visual Studio 中的 IPython REPL | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>在互動式視窗中使用 Python

IPython 模式的 Visual Studio 互動式視窗，是個進階但容易使用的互動式開發環境，且具有「互動式平行計算」功能。 在本主題中，我們會逐步說明在 Visual Studio 互動式視窗中使用 IPython。 您需要安裝 [Anaconda (英文)](https://www.continuum.io) 環境，其中包含 IPython 和必要的程式庫。

> [!Note]
> IronPython 並不支援 IPython，雖然您可以在 [互動式選項] 表單中選取它。 您可以附議此[功能要求 (英文)](https://github.com/Microsoft/PTVS/issues/84) 或自行實作它。

1. 移至 Python 安裝目錄並以 Pylab 模式啟動 IPython，來確認 IPython 封裝已正確安裝：

  ```bash
  ipython --pylab
  ```

1. 輸入下列程式碼：

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. 如果全部都已正確設定，您應該會看到下列結果：

    ![IPython 組態輸出 ](~/python/media/ipython-repl-01.png)

1. 開啟 Visual Studio，切換到 [Python 環境] 視窗 ([檢視] > [其他視窗] > [Python 環境])，然後選取您的 Python 環境。
1. 查看 [pip] 索引標籤，並確保其中已列出 `IPython` 和 `matplotlib`。 如果沒有，請在這裡安裝它們。
1. 選取 [概觀] 索引標籤，選取 [設定互動選項]，將 [互動模式] 設定為 [IPython]，然後選取 [確定]：

    ![將互動模式設定為 [IPython]](~/python/media/ipython-repl-02.png)

1. 選取 [開啟互動式視窗] 以開啟 IPython 模式且搭配 PyLab 的互動式視窗。 如果您才剛剛變更互動模式，您可能需要重設視窗：

    ![IPython 模式的互動式視窗](~/python/media/ipython-repl-03.png)

1. 輸入下列程式碼：

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. 輸入最後一行之後，您應該會看到一個内嵌圖表 (您可以視需要拖曳右下角來調整大小)。

    ![互動式視窗中的內嵌圖表](~/python/media/ipython-repl-04.png)

1. 除了在 REPL 中輸入之外，您可以改為在編輯器中撰寫程式碼，選取它，以滑鼠右鍵按一下，然後選取 [傳送到 Interactive] 命令 (Ctrl-E、E)。 嘗試將以下程式碼貼到編輯器，使用 Ctrl-A 選取它，然後傳送到互動式視窗。 (請注意，當 Visual Studio 將程式碼傳送到互動式視窗時，它會將程式碼以單一單位傳送，以避免產生過渡或部分的圖表)。

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![將程式碼從編輯器傳送至互動式視窗](~/python/media/ipython-repl-05.png)

1. 若要在互動式視窗外查看圖表，請改為使用 [偵錯] > [啟動但不偵錯] 命令來執行程式碼。
    
1. IPython 有多種實用功能，例如逸出到系統殼層、變數替換、擷取輸出等。如需詳細資訊，請參閱 IPython 參考指南：

    ![逸出到系統殼層](~/python/media/ipython-repl-06.png)

1. 您能以「筆記本」模式使用 IPython，這使您可以將任何作業系統上的任何瀏覽器做為畫布使用。 後端 IPython 引擎可在您的本機電腦上，或是在遠端。 Azure 支援[在 Windows 或 Linux VM 上執行 IPython](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook)。 另請參閱 [Azure 筆記本預覽 (英文)](https://notebooks.azure.com)，以在 Azure 上取得免費的「Jupyter 筆記本即服務」：

    ![IPython 筆記本模式](~/python/media/ipython-repl-07.png)

