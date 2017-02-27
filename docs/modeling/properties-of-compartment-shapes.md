---
title: "區間圖案的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.compartmentshape"
helpviewer_keywords: 
  - "網域指定的語言, 區間圖案"
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# 區間圖案的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

區間圖案是一種您可用來顯示以網域特定語言的網域類別圖形。  您可以展開和摺疊區間。  
  
 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 區間圖案具有下列表格中所列的屬性。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|預設值展開摺疊狀態|如果`Expanded`，\[建立時立即顯示的區間。  如果`Collapsed`，它們不是。|Expanded|  
|填滿色彩|此圖形的填滿色彩。|白色|  
|填滿的漸層模式|此圖形的填滿漸層模式。|Horizontal|  
|Geometry|\(矩形或圓角矩形\)，此圖形的幾何。|矩形|  
|具有預設的連接點|如果`True`、 圖形向左，使用上方、 下方、 以及正確的連接點產生的設計工具中。|False|  
|為一個區間標頭為可見|如果`False`，並於圖案有一個路由室，看不到的區間標頭。|True|  
|外框色彩|此圖形的外框色彩。|黑色|  
|外框的虛線樣式|此圖形 \(實線、 虛線，點，DashDot，DashDotDot 自訂\) 的外框虛線樣式。|實心|  
|外框粗細|此圖形的外框粗細。|0.03125|  
|文字色彩|使用此圖形相關聯的文字裝飾的色彩。|黑色|  
|存取修飾詞|區間圖案的存取層級 \(`public`或`internal`\)。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別就會產生這個區間圖案|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述一種 \[區間\] 圖形從產生的原始檔程式碼類別的繼承 \(`none`， `abstract`或`sealed`\)。|None|  
|基底的區間圖案|此圖形的基底類別。|\(無\)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|與此圖形會影響命名空間。|目前的命名空間|  
|工具提示的型別|如何 \(固定的變數或無\) 來定義工具提示。  如果修正，然後值`Fixed Tooltip Text`屬性用做為工具提示。 如果變數，自訂程式碼中定義工具提示。|無|  
|備註|此圖形相關聯的非正式附註。|\<無\>|  
|初始高度|此圖形，以英吋的初始高度。  區間圖案，這是群組首區段的高度，而且無法調整大小。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|公開為屬性的填滿色彩<br /><br /> 公開的填滿漸層模式<br /><br /> 公開為屬性的外框色彩<br /><br /> 公開為屬性的外框的虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開 \(expose\) 的文字色彩|如果`True`，使用者可以設定圖形的 \[敘述\] 屬性。  若要將此設定，以滑鼠右鍵按一下圖形定義，按**加入公開**。|False|  
|描述|用來產生設計工具的文件。|\<無\>|  
|顯示名稱|會產生此圖形設計工具中顯示的名稱。|\<無\>|  
|固定的工具提示文字|適用於固定的工具提示文字。|\<無\>|  
|說明關鍵字|用來製作此圖形的 F1 說明關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)