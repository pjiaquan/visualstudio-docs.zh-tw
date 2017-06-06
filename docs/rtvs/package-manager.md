---
title: "Visual Studio R 工具中的套件管理員 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
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
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>套件管理員

Visual Studio R 工具 (RTVS) 套件管理員是用來管理 R 套件的 UI。 若要開啟它，請選取 [R 工具] > [Windows] > [套件]，或按 Ctrl+7。

套件管理員有三個索引標籤，如下所述。 所有索引標籤都會在左側顯示相關套件清單，並在右側顯示所選取套件的特定詳細資料，包括套件的版本、描述、授權、安裝位置以及其他相關資訊的連結。 右上方的搜尋方塊可讓您篩選清單。

> [!Tip]
> 切換索引標籤時，搜尋方塊中的詞彙仍然會作用。

- [可用的] 可讓您瀏覽要安裝的套件。 如果已經安裝套件，則右側的 [安裝] 按鈕將會變更為 [解除安裝]。

    ![Visual Studio R 工具套件管理員中的 [可用的套件] 索引標籤](media/package-manager-available.png)

- [已安裝的] 會顯示所有已安裝和已載入的套件。 套件旁邊的綠點指出已將它載入至 R 工作階段。 左側清單中的紅色 X 圖示或左側的 [解除安裝] 按鈕，可以用來解除安裝套件。 如果有更新的版本，則已安裝套件右側的藍色向上箭號可更新套件。

    ![Visual Studio R 工具套件管理員中的 [已安裝的套件] 索引標籤](media/package-manager-installed.png)

- [已載入的] 只會顯示載入至 R 工作階段的套件，因此出現時全部都會加上一個綠點。 您也可以在這裡解除安裝和更新套件。

    ![Visual Studio R 工具套件管理員中的 [已載入的套件] 索引標籤](media/package-manager-loaded.png)

## <a name="package-locations"></a>套件位置

套件會安裝到下列位置：

- RTVS 隨附的核心套件會安裝在 `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- 其他套件會安裝到 `%userprofile%\Documents\R\win-library\3.3`

