---
title: "接點的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 接點"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# 接點的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

連接器代表產生的設計工具中的網域關聯性。  
  
 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接器具有下列表格中所列的屬性。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|色彩|此連接器的色彩。|黑色|  
|虛線樣式|\(實線、 虛線、 點、 DashDot、 DashDotDot 或自訂\) 此連接器的線條為虛線樣式。|實心|  
|來源端樣式|此連接器 \(HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或完全沒有\) 來源結束樣式。|None|  
|目標結束樣式|此連接器 \(HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或完全沒有\) 目標結束樣式。|None|  
|文字色彩|使用此連接器相關聯的文字裝飾的色彩。|黑色|  
|Thickness|此項以英吋為單位的連接器線條的粗細。|0.03125|  
|存取修飾詞|類別的存取層級 \(`public`或`internal`\)。|Public|  
|自訂屬性|用來將屬性加入至原始檔程式碼的類別會產生此連接器的。|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|說明來源的程式碼類別從連接器所產生的繼承類型 \(`none`， `abstract`或`sealed`\)。|無|  
|基底的連接器|此連接器基底類別。|\(無\)|  
|名稱|此連接器的名稱。|目前的名稱|  
|命名空間|使用此連接器會影響命名空間。|目前的命名空間|  
|工具提示的型別|如何 \(固定的變數或無\) 來定義工具提示。  如果修正，然後值`Fixed Tooltip Text`屬性用做為工具提示。 如果變數，自訂程式碼中定義工具提示。|\<無\>|  
|備註|此連接器相關聯的非正式附註。|\<無\>|  
|路徑樣式|用於路由的連接器樣式。  A `Rectilinear`連接器可讓直角開啟為必要的。 `Straight`連接器則否。|直線|  
|公開為屬性的色彩<br /><br /> 公開為屬性的虛線樣式<br /><br /> 公開為屬性的厚度<br /><br /> 公開 \(expose\) 的文字色彩|如果`True`，使用者可以設定圖形的 \[敘述\] 屬性。  若要將此設定，以滑鼠右鍵按一下圖形定義，按**加入公開**。|False|  
|描述|用來產生設計工具的文件。|\<無\>|  
|顯示名稱|隨即出現在產生的設計工具中此連接器的名稱。|\<無\>|  
|固定的工具提示文字|適用於固定的工具提示文字。|\<無\>|  
|說明關鍵字|用來製作這個項目的的 F1 說明關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)