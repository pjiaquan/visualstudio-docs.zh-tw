---
title: "幾何圖案的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 54e600e5d626828824d5a2584e1ff4f7fdc09810
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-geometry-shapes"></a>幾何圖案的屬性
若要指定網域類別的執行個體以網域特定語言的顯示方式，您可以使用幾何圖案。 如需詳細資訊，請參閱[如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充定義域專屬語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 幾何圖案具有下表所列的屬性。  
  
|屬性|說明|預設|  
|--------------|-----------------|-------------|  
|填滿色彩|此圖形填滿色彩。|白色|  
|填滿漸層停駐模式|此圖形 （水平、 垂直、 向前對角線、 回溯對角線，或無） 填滿漸層模式。|水平|  
|幾何|此圖形 （矩形、 圓角矩形、 橢圓形或圓形） 的幾何。|矩形|  
|具有預設的連接點|如果`True`、 圖形左邊使用頂端、 底端，並產生的設計工具中的正確的連接點。|False|  
|外框色彩|此圖形的外框色彩。|黑色|  
|外框的虛線樣式|此圖形 （實線、 虛線、 點、 線、 虛線點點或自訂） 的外框虛線樣式。|實線|  
|外框粗細|此圖形的外框粗細。|0.03125|  
|文字色彩|此圖形相關聯的文字裝飾項目所使用的色彩。|黑色|  
|存取修飾詞|（公用或內部） 類別的存取修飾詞。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別產生此圖形。|\<無 >|  
|會產生雙衍生|如果`True`，將會產生基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱[覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂建構函式將會提供在原始程式碼中。 如需詳細資訊，請參閱[覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|說明的繼承來源的程式碼類別產生的圖形的種類 (`none`，`abstract`或`sealed`)。|無|  
|基底的幾何圖形|此圖形的基底類別。|(無)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|與此圖形都相關的命名空間。|目前的命名空間|  
|工具提示的型別|如何 （固定，變數或無） 來定義工具提示。 然後固定的值如果`Fixed Tooltip Text`屬性做為工具提示，如果變數，則為工具提示會定義自訂程式碼中。|無|  
|備註|這個項目相關聯的非正式附註。|\<無 >|  
|初始高度|此圖形，以英吋的初始高度。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|當做屬性公開的填滿色彩<br /><br /> 公開的填滿漸層停駐模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框的虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開 （expose) 的文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要將此設定，以滑鼠右鍵按一下圖形的定義，然後按一下**加入已公開**。|False|  
|描述|描述用來產生的設計工具的文件。|\<無 >|  
|顯示名稱|將此圖形產生的設計工具中顯示的名稱。|\<無 >|  
|固定的工具提示文字|使用固定的工具提示文字。|\<無 >|  
|說明關鍵字|用來製作此圖形的 F1 說明關鍵字。|\<無 >|  
  
## <a name="see-also"></a>另請參閱  
 [定義域專屬語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
