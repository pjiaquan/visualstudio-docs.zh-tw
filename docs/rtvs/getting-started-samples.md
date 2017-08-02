---
title: "Visual Studio R 工具的範例專案 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
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
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio R 工具範例專案

此範例集合能讓您開始使用 R、Visual Studio R 工具 (RTVS) 和 Microsoft R 伺服器︰

1. 下載[ ZIP 檔案範例](https://github.com/Microsoft/RTVS-docs/archive/master.zip)並解壓縮至您選擇的資料夾。
1. 開啟 `examples/Examples.sln`；您會看到專案中的兩個資料夾︰

    - *初探 R* 為 R 新手提供合適的簡介。
    - *MRS 和機器學習服務*提供如何使用 R 和 Microsoft R 伺服器進行機器學習服務的範例。

## <a name="a-first-look-at-r"></a>初探 R

這個範例透過原始程式檔中的大量註解，提供 R 的深入介紹。 體驗兩者的最好方法是將游標放在檔案頂端，然後按 Ctrl + Enter 鍵逐一地將每一行傳送到 [R 互動] 視窗，您可以在其中看到結果。 請注意，有幾行會安裝套件，可能需要幾分鐘的時間。

- `1-Getting Started with R.R` 涵蓋許多 R 基本概念，包括使用套件、載入和分析資料，以及繪製。

    ![1-Getting Started with R.R 範例的範例輸出](~/docs/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` 介紹 ggplot2 圖形套件，它是以視覺效果豐富的繪圖和簡單的語法而知名。 這個範例可以視覺化斐濟的地震資料。

    ![2-Introduction to ggplot2.R 範例的範例輸出](~/docs/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R 伺服器和機器學習服務

此範例集合示範如何使用 R 和 Microsoft R 伺服器建立機器學習服務模型，以及如何充分利用 [Microsoft R 伺服器 (MRS)](http://aka.ms/rtvs-msft-r) 的功能。 請注意，您必須安裝 MRS 才能在標題與註明處中使用 `MRS` 來執行指令碼。

如同所有範例，體驗它們的好方法是開啟檔案、將游標放在最上方，然後使用 Ctrl + Enter 鍵逐步執行程式碼行。 如需詳細資訊，另請參閱每個資料夾中的 markdown 檔案。

- `Benchmarks` 會執行許多大量運算的基準測試，顯示透過使用 Microsoft R Open 和 Intel 數學核心程式庫 (MKL) 的快速、平行線性代數計算而可能會提升的效能。 使用模擬的資料，它特別會比較兩個執行緒與針對特定矩陣相關計算使用一個執行緒的情況。   

    ![範例基準測試繪圖](~/docs/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` 會建立單車出租的需求預測模型，這是使用 Microsoft R 伺服器，並以歷程記錄資料集為基礎。 

- `Data_Exploration` 包含三個指令碼：  
    - `Import Data from URL.R` 示範如何將 URL 識別資料檔案載入到 R。
    - `Import Data from URL to xdf.R` 示範如何將 URL 識別資料檔案作為 xdf 載入到 Microsoft R 伺服器。 (需要 MRS。)
    - `Using ggplot2.R` 是 `A First Look at R/2-Introduction to ggplot2.R` 範例的延伸模組，提供更豐富的 ggplot2 功能教學課程，包括互動式 3D 繪圖。

        ![Using ggplot2.R 範例的輸出](~/docs/rtvs/media/samples-3d-interactive.png)

- `Datasets` 包含其他範例所使用的三個 `.csv`檔案
- `Flight_Delays_Prediction_with_R` 和 `Flight_Delays_Prediction_with_MRS` 示範如何使用 R、機器學習服務和歷史準點率和天候資料預測航班誤點。 
- `Machine learning` 包含三個範例，用來學習如何預測航班誤點、住宿價格和單車出租，並示範將 R 和 MRS 應用到真實世界的問題。 它們還要告訴您如何使用數個常用的機器學習模型，並使用 [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) 工作區將其部署為 Azure Web 服務。

- `R_MRO_MRS_Comparison` 是六個部分的比較，顯示 R、Microsoft R Open 和 Microsoft R 伺服器在命令、語法、建構和效能方面的相似性和差異。

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Microsoft R Open 與 Microsoft R 伺服器有什麼特別之處？

[Microsoft R Open](http://aka.ms/rtvs-r-open)，是 Microsoft 的 R 發行版本，它與 [CRAN R](https://cran.r-project.org/) 的不同有兩個重要的方面︰

1. 搭配 [Intel Math Kernel Library](https://software.intel.com/intel-mkl) (Intel 數學核心程式庫) 使用時[計算效能較高](https://mran.revolutionanalytics.com/rro/#intelmkl1)。 這些可以從 Microsoft 免費下載，以便搭配 Microsoft R Open 使用。

1. [可重製的 R 工具箱](https://mran.revolutionanalytics.com/rro/#reproducibility)，它能確保您用來建置 R 程式的程式庫一律能供想要重製您的作品的其他人使用。

[Microsoft R 伺服器](http://aka.ms/rtvs-msft-r)是可讓您處理更多資料，並更快速處理的 R 延伸模組。 它提供 R 兩項強大的功能︰

1. 較大的資料集。 MRS 可以處理來自各種來源的記憶體不足資料，包括 Hadoop 叢集、資料庫和資料倉儲。 您永遠不必再受限於記憶體。

1. 平行、多核心處理程序。 MRS 可以有效率地將計算分散到它能用的所有計算資源。 在您的個人工作站或遠端叢集上，MRS 會更快獲得解答。

下列比較顯示在特定矩陣計算方面，MRS 和具有 MKL 的 MRO 計算效能明顯優於 R 和沒有 MKL 的 MRO。 這項計算中，會使用模擬的資料︰

![比較 MRS 和使用 MKL 的 MRO，以及 R 和沒有 MKL 的 MRO](~/docs/rtvs/media/samples-speed-comparison.png)

如需 R 與 MRO 和 MRS 的技術比較，請參閱 [Lixun Zhang 關於這主題的詳細討論](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html)。

然後，下圖比較建立使用羅吉斯迴歸模型來預測預定客機航班的抵達是否將延遲超過 15 分鐘時，耗用的時間 (以秒為單位)。 當增加少量的資料列時，CRAN R 中使用的已耗用時間會大幅增加，而 MRS 則只增加大約兩倍。 如需此基準測試的詳細資料，請參閱 `Benchmarks/rxGlm_benchmark.R` 範例。

![rxGlm 基準測試](~/docs/rtvs/media/samples-rxGLM-benchmark.png)

