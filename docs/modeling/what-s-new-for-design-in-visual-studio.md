---
title: "在 Visual Studio 中設計的最新消息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>在 Visual Studio 中設計的最新消息

## <a name="live-dependency-validation"></a>即時相依性驗證

移除不必要的相依性是管理您的技術負債很重要的一部分。
相依性的即時驗證現在包含，提供精確的資訊有關的問題，且可完全從錯誤清單和編輯器中的新功能。

![作用中的即時相依性驗證](~/modeling/media/dep-validation-whatsnew-01.png)

撰寫經驗已進行相依性驗證更容易找到和更容易存取，變更從 「 圖層圖表 」 至 「 相依性圖表 」 的術語。

**架構**功能表現在包含直接建立相依性圖表的命令︰

![在 [架構] 功能表上的即時相依性項目](~/modeling/media/dep-validation-whatsnew-02.png)

...且已變更之屬性名稱的相依性圖表，而其描述中的圖層，讓它們更有意義︰

![即時更新的相依性屬性名稱](~/modeling/media/dep-validation-whatsnew-03.png)

您現在看到立即在目前方案中的程式碼的分析結果中變更的影響每次儲存圖表。 您不必再等待完成 「 驗證相依性 」 命令。

如需詳細資訊，請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。 
 
## <a name="uml-designers-have-been-removed"></a>已移除 UML 設計工具

UML 設計工具已移除了此版本的 Visual Studio 企業版。

* UML 圖表現在會顯示為 XML 檔案
* UML 模型總管 不存在
* 模型的專案的參考不會再用於相依性驗證
* 不會再顯示 [方案總管] 中的 [圖層參考] 節點
* 不再使用相依性 （層次） 圖表上的 「 驗證 」 建置動作-已移除建置工作 
* 版本之間的往返並維護專案結構
* 您仍可以開啟、 建立、 編輯及相依性 （層次） 圖表儲存為 XML
* 連結至相依性 （層次） 圖表的 TFS 工作項目不能在設計介面上存取
* 不再支援反向連結從 DSL 或圖層 
* UML 擴充性模型 SDK 中的已不再支援

不過，支援視覺化.NET 和 c + + 程式碼的架構是可透過[code map](map-dependencies-across-your-solutions.md)，和前述的相依性驗證明顯的改進。

如果您是大量 UML 設計工具的使用者，您可以繼續使用 Visual Studio 2015 或更早版本，而您決定 UML 需求的替代工具。

如需詳細資訊，請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Architecture and Modeling Tools 的版本支援  

Visual Studio 有數個版本。 並非所有版本都提供 Architecture and Modeling Tools 的支援。 下表顯示每個工具的可用性。  
  
|**功能**|**企業**|**專業版**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Code map**|是|請參閱附註 (1)|-|-|  
|**相依性圖表**|是|請參閱附註 (2)|請參閱附註 (2)|-|  
|**導向圖形**（DGML 圖表）|是|是|是|-|  
|**程式碼複製**|是|-|-|-|  
  
注意 (1)：僅支援讀取程式碼對應、篩選程式碼對應、加入新的泛型節點，及從選取範圍建立新的導向圖形。

附註 (2): 僅支援讀取相依性圖表。

