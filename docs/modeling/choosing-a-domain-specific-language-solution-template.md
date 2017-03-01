---
title: "選擇網域指定的語言方案範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-domain-specific-language-solution-template"></a>選擇網域指定的語言方案範本
若要建立定義域專屬語言方案，選擇一個網域特定語言設計工具精靈 中的方案範本。 藉由選擇最接近的語言，您想要建立的範本，您可以減少您必須對起始方案的修改。  
  
 定義域專屬語言設計工具精靈 中提供下列方案範本。  
  
|範本|功能|描述|  
|--------------|--------------|-----------------|  
|類別圖表|-區間圖形<br />類別繼承<br />-關聯性繼承<br />圖形繼承<br />-關聯性屬性|如果您的網域特定語言包括實體和關聯性具有屬性，請使用這個方案範本。 此範本會建立類似於 UML 類別圖的定義域專屬語言。 主要實體的類別和介面，以及關聯、 一般化和實作的關聯性。 類別或介面顯示為方塊，其中包含的屬性清單。|  
|元件圖表|-連接埠|如果定義域專屬語言包括元件，也就是軟體系統組件，請使用這個方案範本。 此範本會建立類似於 UML 元件圖的定義域專屬語言。 主要實體為元件和連接埠，而外部元件的小圖形的形式出現。|  
|工作流程圖表|-映像和幾何形狀<br />-   *區隔線*|如果您的網域特定語言包含工作流程、 狀態或順序，請使用這個方案範本。 此範本會建立類似於 UML 活動圖表的定義域專屬語言。 主要實體是一項活動，而主要的關聯性活動之間的轉換。 範本包含數個開始狀態、 最終狀態，等同步處理列的項目。|  
|最小語言|-一個類別和圖形<br />-一的關聯性和連接器|如果您的網域特定語言不類似於其他範本，請使用這個方案範本。 此範本會建立具有兩個類別和一個關聯性，以表示定義域專屬語言**工具箱**為**方塊**和**列**。 類別和關聯性都有一個範例字串屬性。|  
|最小 WinForm 設計工具|-A 小型的模型。<br />-顯示模型 Windows Form。|如果您想要建置應用程式中的 DSL 繫結至 Windows Form，而非圖形設計工具，請使用此範本。<br /><br /> 做為語言的使用者介面表單是 Dsl\UI 資料夾中。<br /><br /> 開啟表單設計工具之前，您應該建置專案。<br /><br /> 如需詳細資訊，請參閱[建立 Windows Forms-Based 定義域專屬語言](../modeling/creating-a-windows-forms-based-domain-specific-language.md)。|  
|最小 WPF 設計工具|-A 小型模型<br />-顯示模型 Windows Presentation Foundation 使用者介面|如果您想要建置應用程式中的 DSL 繫結 WPF 使用者介面，而不是圖形的設計工具，請使用此範本。<br /><br /> 使用者介面的設計工具是 Dsl\UI 資料夾中。<br /><br /> 開啟 UI 設計工具之前，您應該建置專案。<br /><br /> 如需詳細資訊，請參閱[建立 WPF-Based 定義域專屬語言](../modeling/creating-a-wpf-based-domain-specific-language.md)。|  
|DSL 程式庫|-A 最少的程式庫|如果您想要建立部分的 DSL 定義可以匯入其他 DSL 定義，請使用此範本。|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)

