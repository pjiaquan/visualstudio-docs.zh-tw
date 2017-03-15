---
title: "讀取模型和其他 Visual Studio 版本中的圖表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 20
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
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 9ffc4c39dee2da1d6daa051f478eac18d9670151
ms.lasthandoff: 02/22/2017

---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中讀取模型和圖表
在不支援模型建立的 Visual Studio 版本中開啟模型時，會以唯讀模式開啟模型。 在此模式中，您可以變更圖表的版面配置，但是無法變更模型。  
  
 若要查看哪些版本的 Visual Studio 支援模型建立，請參閱[的架構和模型工具版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>取得模型和圖表的存取權  
 若要讀取相依性圖表，您必須先使用 Visual Studio 開啟模型專案中，然後再開啟 圖表。  
  
 基於這個理由，如果您想要讀取相依性圖表中，您也必須建立所在的模型專案的存取權。 從 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] 存取專案，或取得專案檔複本，即可完成這項作業。  
  
> [!NOTE]
>  這不適用於透過程式碼產生的 Code Map 和 .NET 類別圖。 這些圖表可以與模型專案分開檢視。  
  
 若要讀取相依性圖表，您需要的檔案的最小集如下︰  
  
-   兩個圖表的圖表，例如，想要讀取的檔案**MyDiagram.classdiagram 和 MyDiagram.classdiagram.layout**。  
  
    > [!NOTE]
    >  如需相依性圖表，您還應檔為*MyDiagram***。 layerdiagram.suppressions**。  
  
-   模型專案檔 (**MyModel.modelproj**)  
  
-   根模型檔 (**ModelDefinition\MyModel.uml**)  
  
-   在圖表中所參考之任何套件的套件檔案 (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>您可以在唯讀模式中進行的變更  
 如果您在不支援模型建立的 Visual Studio 版本中開啟模型和其圖表，則無法變更模型。 也就是說，您無法變更圖表或模型總管中所顯示的項目和關聯性。 不過，您可以對圖表的版面配置進行一些變更：  
  
-   重新排列圖表上的圖形和連接器。  
  
-   展開和摺疊圖形。  
  
 您可以儲存這些變更。 如果您想要讓其他使用者看到您的變更，您必須至少傳送更新**.layout**檔案。  
  
##  <a name="a-namerelatedtopicsa-related-topics"></a><a name="RelatedTopics"></a>相關的主題  
  
|標題|說明|  
|-----------|-----------------|  
|[相依性圖表︰ 參考](../modeling/layer-diagrams-reference.md)|分層圖會顯示現有或提議之架構的結構。 撰寫程式碼時，可以針對分層圖自動進行驗證。|  
  
## <a name="see-also"></a>另請參閱  
 [建立應用程式模型](../modeling/create-models-for-your-app.md)
