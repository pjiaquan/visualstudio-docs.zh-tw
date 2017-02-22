---
title: "通訊埠圖案的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.port"
helpviewer_keywords: 
  - "網域指定的語言, 通訊埠圖案"
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 通訊埠圖案的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用連接埠圖形以代表網域類別在產生的設計工具中。  
  
 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接埠圖形具有下列表格中所列的屬性。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|填滿色彩|此圖形的填滿色彩。|白色|  
|填滿的漸層模式|此圖形的填滿漸層模式。|Horizontal|  
|Geometry|\(矩形、 圓角矩形、 橢圓形或圓形\) 此圖形的幾何。|矩形|  
|具有預設的連接點|如果`True`、 圖形向左，使用上方、 下方、 以及正確的連接點產生的設計工具中。|False|  
|外框色彩|此圖形的外框色彩。|黑色|  
|外框的虛線樣式|此圖形 \(實線、 虛線、 點、 DashDot、 DashDotDot 或自訂\) 的外框虛線樣式。|實心|  
|外框粗細|此圖形的外框粗細。|0.03125|  
|文字色彩|適用於此圖形相關聯的文字裝飾的色彩。|黑色|  
|存取修飾詞|類別的存取層級 \(`public`或`internal`\)。|Public|  
|自訂屬性|用來將屬性加入至這個圖形可產生來源的程式碼類別。|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱[覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|說明了從連接埠就會產生的原始檔程式碼類別的繼承類型 \(`none`， `abstract`或`sealed`\)。|無|  
|基底連接埠|此圖形的基底類別。|\(無\)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|與此圖形會影響命名空間。|目前的命名空間|  
|工具提示類型|如何 \(固定的變數或無\) 來定義工具提示。  如果修正，然後值`Fixed Tooltip Text`屬性用做為工具提示。 如果變數，自訂程式碼中定義工具提示。|無|  
|備註|此圖形相關聯的非正式附註。|\<無\>|  
|初始高度|此圖形，以英吋的初始高度。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|公開為屬性的填滿色彩<br /><br /> 公開的填滿漸層模式<br /><br /> 公開為屬性的外框色彩<br /><br /> 公開為屬性的外框的虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開 \(expose\) 的文字色彩|如果`True`，使用者可以設定圖形的 \[敘述\] 屬性。  若要將此設定，以滑鼠右鍵按一下圖形定義，按**加入公開**。|False|  
|描述|用來產生設計工具的文件。|\<無\>|  
|顯示名稱|會產生此圖形設計工具中顯示的名稱。|\<無\>|  
|固定的工具提示文字|適用於固定的工具提示文字。|\<無\>|  
|說明關鍵字|用來製作此圖形的 F1 說明關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)