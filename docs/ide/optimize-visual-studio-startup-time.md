---
title: "最佳化 Visual Studio 啟動時間 | Microsoft Docs"
ms.custom: 
ms.date: 01/09/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 27a265dbbb1f9426ba2dd254095c84239bbd0db7
ms.lasthandoff: 03/07/2017

---
# <a name="optimize-visual-studio-startup-time"></a>最佳化 Visual Studio 啟動時間
在理想情況下，Visual Studio 應該一律盡快啟動。 不過，Visual Studio 延伸模組和開啟工具視窗是在啟動時自動載入，因此可能會嚴重影響啟動時間。 [管理 Visual Studio 效能] 視窗不只可讓您看到影響 Visual Studio 啟動時間的延伸模組和功能，還可讓您決定其載入行為，以進一步控制 Visual Studio 的啟動速度。

## <a name="control-startup-behavior"></a>控制啟動行為

為了避免延長啟動時間，Visual Studio 2017 會使用依需求載入方式，以避免在啟動時載入擴充功能。 這表示延伸模組不會在 Visual Studio 啟動之後立即開啟，而是在啟動之後視需要非同步開啟。 此外，因為在先前的 Visual Studio 工作階段中保持開啟的工具視窗可能會讓啟動時間變慢，所以 Visual Studio 會以更智慧的方式開啟工具視窗，以避免影響啟動時間。

如果 Visual Studio 偵測到啟動變慢，就會出現快顯訊息，警告您導致速度變慢的延伸模組或工具視窗。 此訊息也會提供 [管理 Visual Studio 效能] 對話方塊的連結，而在此對話方塊中，會列出影響啟動效能的延伸模組和工具視窗。 這個對話方塊可讓您變更延伸模組和工具視窗設定，以改善啟動效能。

![管理 Visual Studio 效能 - 快顯視窗](../ide/media/vside_perfdialog_popup.PNG "管理 Visual Studio 效能 - 快顯視窗")

[管理 Visual Studio 效能] 對話方塊有兩種分類︰[延伸模組] 和 [工具視窗]。

### <a name="control-extensions"></a>控制延伸模組
如果延伸模組讓 Visual Studio 啟動變慢，則在您選擇其中一種延伸模組類型時，該延伸模組會出現在 [管理 Visual Studio 效能] 對話方塊中。 如果對啟動時間的影響 (列在 [影響] 區段下) 過高，您可以選擇 [停用] 按鈕來選擇一律在啟動時停用延伸模組。 您可以使用延伸模組管理員或 [管理 Visual Studio 效能] 對話方塊，針對未來的工作階段重新啟用延伸模組。

![管理 Visual Studio 效能 - 延伸模組](../ide/media/vside_perfdialog_extensions.PNG "管理 Visual Studio 效能 - 延伸模組")

除了啟動延伸模組之外，您也可以停用在載入方案時或使用者輸入時所載入的延伸模組。 只要選擇案例，就可以查看相關聯延伸模組的清單。

### <a name="control-tool-windows"></a>控制工具視窗
如果工具視窗會讓 Visual Studio 啟動變慢，您可以選擇保留其預設行為 (這對啟動速度沒有任何用處)，也可以選擇兩種行為中的其中一種行為來覆寫其行為：

- **啟動時不要顯示視窗**：如果您選擇此選項，則一律會在開啟 Visual Studio 時關閉指定的工具視窗，即使已在前一個工作階段中開啟也是一樣。 您可以從功能表開啟工具視窗。
- **啟動時自動隱藏視窗**：如果已在前一個工作階段中開啟工具視窗，則選擇此選項會在啟動時摺疊工具視窗的群組，以避免初始化工具視窗。 如果您經常使用工具視窗，則這是不錯的選擇，原因是工具視窗仍然可用，但不再對 Visual Studio 啟動時間造成負面影響。

![管理 Visual Studio 效能 - 工具視窗](../ide/media/vside_perfdialog_toolwindows.PNG "管理 Visual Studio 效能 - 工具視窗")

如果您稍後改變心意，則可以在 [管理 Visual Studio 效能] 對話方塊中還原所有這些選項。 若要開啟 [管理 Visual Studio 效能] 對話方塊，請在功能表列上依序選擇 [說明] 和 [管理 Visual Studio 效能]。

## <a name="speed-up-solution-load"></a>加速方案載入

Visual Studio 2017 導入一項稱為「輕量型解決方案載入」的新功能，可減少在 IDE 中載入大型方案所需的時間量和記憶體數量。 如果您有包含許多 C#、VB 或 C++ 專案的大型方案，則可能會在啟用輕量型解決方案載入時看到大幅效能改善。

因為某些 IDE 功能在啟用輕量型解決方案時不是完全可用，所以預設會關閉此功能。 下列各節將協助您決定是否不要啟用這項功能。

### <a name="enable-lightweight-solution-load"></a>啟用輕量型解決方案載入

您可以啟用整個 IDE 或個別方案的輕量型解決方案載入。 若要啟用整個 IDE 的輕量型解決方案載入，請依序移至 [工具] 和 [選項]，然後移至 [專案和方案] 區段。

![工具選項對話方塊](../ide/media/VSIDE_LightweightSolutionLoad.png)

若要啟用個別方案的輕量型解決方案載入，請選擇方案總管中的頂層方案節點。  在 [屬性] 視窗中，選擇下列其中一個 [輕量型載入] 屬性值。

- **已啟用**：不論整個 IDE 設定為何，都會啟用此方案的輕量型解決方案載入。
- **已停用**：不論整個 IDE 設定為何，都會停用此方案的輕量型解決方案載入。
- **預設**：輕量型解決方案載入行為將會延後到整個 IDE 設定。

![底下提供說明，包括方案總管](../ide/media/VSIDE_LSL Solution Setting.png)

變更輕量型解決方案載入設定時，變更會在下一次載入方案時生效。 您不需要重新啟動 IDE。

### <a name="automatically-enable-lightweight-solution-load"></a>自動啟用輕量型解決方案載入

當您在 Visual Studio 2017 中開啟大型方案時，可能會看到啟用輕量型解決方案載入的快顯訊息。 只有包含許多 C#、VB 或 C++ 專案的方案，才會出現此訊息。 選擇 [啟用] 命令只會對該方案啟用輕量型解決方案載入。 將不會變更整個 IDE 設定。

![快顯視窗](../ide/media/VSIDE_LSL Popup.png)

您稍後可以在方案的 [屬性] 視窗中停用輕量型解決方案載入。

### <a name="lightweight-solution-load-limitations"></a>輕量型解決方案載入限制
啟用輕量型解決方案載入時，就可以完全使用 IDE 的大部分功能。 不過，某些 IDE 功能和協力廠商延伸模組可能無法完全相容。  啟用輕量型解決方案載入時，已知下列功能無法運作︰

#### <a name="third-party-extensions"></a>協力廠商延伸模組
在輕量型解決方案載入已啟用時，有些延伸模組的行為可能不如預期。

#### <a name="edit-and-continue"></a>編輯後繼續
在您開始偵錯時未載入的專案中無法使用 [編輯後繼續]。 這類專案中包含的檔案將會是唯讀的，而且將會回報錯誤，指出嘗試編輯時尚未載入專案。

#### <a name="f-support"></a>F# 支援
在啟用輕量型解決方案負載時，F# 專案可能無法正確建置，且符號在「移至」中可能不會完全可用。

