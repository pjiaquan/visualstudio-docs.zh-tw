---
title: "擴充相依性圖表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>擴充相依性圖表
您可以撰寫程式碼來建立和更新相依性圖表，並驗證您對 Visual Studio 中的相依性圖表的程式碼的結構。 您可以加入出現在圖表的捷徑 (操作) 功能表中的命令、自訂拖放軌跡，以及從文字範本存取圖層模型。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。  
  
 如需相依性圖表的詳細資訊，請參閱︰  
  
-   [相依性圖表︰ 參考](../modeling/layer-diagrams-reference.md)  
  
-   [相依性圖表︰ 方針](../modeling/layer-diagrams-guidelines.md)  
  
-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> 需求  
 您必須在想要開發圖層擴充功能的電腦上安裝下列項目：  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modeling SDK for Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 您必須在想要執行圖層擴充功能的電腦上安裝適合的 Visual Studio 版本。 如需詳細資訊，請參閱[部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)。  
  
 若要查看哪些版本的 Visual Studio 支援相依性圖表，請參閱[的架構和模型工具版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="in-this-section"></a>本章節內容  
 [將命令和軌跡加入至相依性圖表](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [相依性圖表中加入自訂架構驗證](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [將自訂屬性加入至相依性圖表](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [巡覽及更新程式碼中的圖層模型](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)  
  
 [疑難排解擴充功能的相依性圖表](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>另請參閱  
 [定義與安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)   
 [相依性圖表︰ 參考](../modeling/layer-diagrams-reference.md)   
 [相依性圖表︰ 方針](../modeling/layer-diagrams-guidelines.md)   
 [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)   
 [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)   

