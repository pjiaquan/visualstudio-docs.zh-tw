---
title: "分析和模型架構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>分析架構並製作架構模型
請確定您的應用程式所使用 Visual Studio 架構與模型工具來設計和模型化應用程式符合架構需求。 

* 您可以使用 Visual Studio 視覺化程式碼的架構、行為和關聯性，更輕鬆地了解現有的程式碼。 

* 教育您的小組需要尊重架構相依性。  
  
* 請在開發過程中，於整個應用程式生命週期的不同詳細資料層級建立模型。

請參閱[案例︰ 變更您的設計使用視覺化和模型化](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)。  
  
## <a name="to"></a>以  
  
|||  
|-|-|  
|**視覺化程式碼**：<br /><br /> -藉由建立 code map，請參閱程式碼的組織和關聯性。 將組件、命名空間、類別、方法等之間的相依性視覺化。<br />-從程式碼建立類別圖，請參閱類別結構和特定專案的成員。<br />-建立相依性圖表來驗證程式碼來尋找您的程式碼和它的設計之間的衝突。|-   [視覺化程式碼](../modeling/visualize-code.md)<br />-   [使用類別和其他類型 （類別設計工具）](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [視訊︰ 了解使用 Visual Studio 2015 code map 的程式碼的設計](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [視訊︰ 驗證即時架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**定義架構**：<br /><br /> 定義和強制執行您的程式碼，藉由建立相依性圖表元件之間的相依性的條件約束。|-   [視訊︰ 驗證架構相依性，使用 Visual Studio （第 9 頻道）](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**驗證您的系統需求和預定設計︰**<br /><br /> 驗證程式碼相依性，以描述預定的架構的相依性圖表，並防止可能會與設計衝突的變更。|-   [視訊︰ 驗證架構相依性，使用 Visual Studio （第 9 頻道）](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**使用 Team Foundation 版本控制，共用模型、圖表和 Code Map**：<br /><br /> -放 code map、 專案和 Team Foundation 版本控制下的 deoendency 圖表，您可以共用它們。|當多位使用者在 Team Foundation 版本控制使用這些項目時，請使用下列方針協助您避免版本控制問題：<br /><br /> -   [管理模型與版本控制下的圖表](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**自訂模型和圖表**：<br /><br /> 建立您自己的定義域專屬語言。|-   [Modeling SDK for Visual Studio-定義域專屬語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**使用 T4 範本產生文字**：<br /><br /> -使用文字區塊和控制邏輯內部範本產生文字為基礎的檔案。<br /> -使用 Visual Studio 中包含的 MSBuild T4 範本建置|-   [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)|

若要查看哪些版本的 Visual Studio 支援每項功能，請參閱[的架構和模型工具版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>模型的類型及其用法  
  
|**模型類型和一般用法**|  
|-------------------------------------|  
|**Code map**<br /><br /> Code Map 可協助您查看程式碼中的組織和關聯性。<br /><br /> 一般用法：<br /><br /> 檢查程式碼以便進一步瞭解其結構和其相依性，如何更新，以及估計的成本提議的變更。<br /><br /> 請參閱：<br /><br /> -   [對應整個方案的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [找出潛在的問題使用 code map 分析器](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**相依性圖表**<br /><br /> 相依性圖表可讓您定義一組圖層或區塊有明確的相依性的應用程式結構。 您可以執行驗證，以找出程式碼中的相依性和相依性圖表中描述的相依性之間的衝突。<br /><br /> 一般用法：<br /><br /> -穩固其結構透過多次變更應用程式的存留期間。<br />然後再簽入變更的程式碼探索意外的相依性衝突。<br /><br /> 請參閱：<br /><br /> -   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [相依性圖表︰ 參考](../modeling/layer-diagrams-reference.md)<br />-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|  
|**定義域專屬語言 (DSL)**<br /><br /> DSL 是您為特定目的所設計的標記法。 在 Visual Studio 中，通常會以圖形表示。<br /><br /> 一般用法：<br /><br /> 產生或設定應用程式的組件。 開發標記法和工具必須進行一些工作。 此結果會比自訂 UML 更適用您的定義域。<br />-若為大型專案或其中的投資開發 DSL 及其工具由多個專案中使用的產品線。<br /><br /> 請參閱：<br /><br /> -   [Modeling SDK for Visual Studio-定義域專屬語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>哪裡可以取得詳細資訊？  
  
[Visual Studio Visualization i 模型化工具論壇](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>另請參閱  
 [最新消息](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [開發和應用程式生命週期管理](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

