---
title: "泳道的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "網域指定的語言, 泳道"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 泳道的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以新增至圖表的區隔線。  區隔線分為垂直或水平區域的圖表。  您可以定義要顯示在 \[區隔線內的其他圖形。  如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 區隔線具有下列表格中所列的屬性。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|本文填滿色彩|本文的區隔線所填滿色彩。|白色|  
|標題填滿色彩|泳道標頭的填滿色彩。|DarkGray|  
|分隔頁色彩|在分隔線色彩。|LightGray|  
|分隔的線條樣式|The style of the separator line \(`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, or `Custom`\).|`Dash`|  
|分隔符號厚度|分隔線，以英吋的粗細。|0.03125|  
|文字色彩|適用於此區隔線相關聯的文字裝飾的色彩。|黑色|  
|存取修飾詞|類別的存取層級 \(`public`或`internal`\)。|Public|  
|自訂屬性|用來將屬性加入至程式碼由這個區隔線所產生的類別。|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述一種由區隔線所產生的原始檔程式碼類別的繼承 \(`none`， `abstract`或`sealed`\)。|無|  
|基底的區隔線|此區隔線基底類別。|\(無\)|  
|名稱|此區隔線的名稱。|目前的名稱|  
|命名空間|與此區隔線相關的命名空間。|目前的命名空間|  
|工具提示的型別|定義工具提示的方式 \(`fixed`， `variable`，或`none`\)。  如果`fixed`，然後值`Fixed Tooltip Text`屬性則使用。 如果`variable`，然後在 \[自訂程式碼定義工具提示。|\<無\>|  
|備註|此區隔線相關聯的非正式附註。|\<無\>|  
|對齊方式|水平或垂直對齊方式。|垂直|  
|初始高度|此區隔線，以英吋的初始高度。  僅能套用至水平的區隔線。|0|  
|初始寬度|此區隔線，以英吋的初始寬度。  僅能套用至垂直的區隔線。|0|  
|公開 \(expose\) 的文字色彩|如果`True`，使用者可以在產生的設計工具中設定的區隔線色彩。  若要將此設定，\[區隔線\] 圖形上按一下滑鼠右鍵，按一下**加入公開**。|False|  
|描述|用來產生設計工具的文件。|\<無\>|  
|顯示名稱|會顯示在 \[產生的設計工具，來參考此區隔線類別名稱。|\<無\>|  
|固定的工具提示文字|適用於固定的工具提示文字。|\<無\>|  
|說明關鍵字|用來製作此區隔線的 F1 說明關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)