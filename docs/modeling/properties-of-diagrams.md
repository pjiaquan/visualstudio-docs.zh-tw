---
title: "圖表的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "網域指定的語言, 圖表"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# 圖表的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以設定指定圖表中產生的設計工具的顯示方式的屬性。  比方說，您也可以在圖表中指定文字的預設色彩。  
  
 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 下表列出了圖表的屬性。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|填滿色彩|圖表的填滿色彩。|白色|  
|文字色彩|隨即出現在圖表的文字色彩。|黑色|  
|存取修飾詞|\(公用或內部\) 類別的存取修飾詞。|Public|  
|自訂屬性|用來將屬性加入至產生的程式碼的類別。|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|說明來源的程式碼類別圖表中所產生的繼承類型 \(`none`， `abstract`或`sealed`\)。|None|  
|基底的圖表|這張圖表的基底類別。|\(無\)|  
|名稱|此圖表的名稱。|目前的名稱|  
|命名空間|使用這個圖表會影響命名空間。|目前的命名空間|  
|表示類別|根網域類別，表示這個圖表。|目前的根類別如果有的話|  
|備註|這個項目相關聯的非正式附註。|\<無\>|  
|公開為屬性填入色彩|如果`True`，使用者可以設定產生的設計工具\] 的圖表的填滿色彩。  若要將此設定，\[圖表\] 圖形上按一下滑鼠右鍵，按一下**新增 Explosed**。|False|  
|公開 \(expose\) 為屬性的文字色彩|如果`True`，使用者可以在產生的設計工具中設定圖表的文字色彩。  若要將此設定，\[圖表\] 圖形上按一下滑鼠右鍵，按一下**新增 Explosed**。|False|  
|描述|描述用來產生設計工具的文件。|\<無\>|  
|顯示名稱|將產生的設計工具，這個圖表中顯示的名稱。|\<無\>|  
|說明關鍵字|用來製作這個圖表的 F1 說明關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)