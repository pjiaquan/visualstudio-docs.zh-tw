---
title: "Decorator 的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, Decorator"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Decorator 的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

裝飾是圖示\]、 \[文字\] 或 \[展開\/摺疊 ＞ 形箭號，可能會出現在 \[圖形\] 或 \[在圖表上的連接器。  下表說明三種類型的裝飾的屬性。  某些屬性可能會出現圖形裝飾只或只有在連接器裝飾上。  
  
 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
## 展開\/摺疊裝飾  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|DisplayName|會顯示在 \[產生的設計工具裝飾名稱。|展開摺疊裝飾|  
|名稱|裝飾名稱。|ExpandCollapseDecorator|  
|備註|這個裝飾相關聯的非正式附註。|\<無\>|  
|HorizontalOffset|水平位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|VerticalOffset|垂直位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|OffsetFromLine|從列，相對於它的預設位置，以英吋裝飾的位移。  \(在連接器只。\)|0|  
|OffsetFromShape|相對於它的預設位置，以英吋為單位指定圖案裝飾的位移。  \(在連接器只。\)|0|  
|Position|裝飾的預設位置。|SourceTop|  
  
## 圖示裝飾  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|DefaultIcon|要顯示的圖示或影像檔的路徑。|\<無\>|  
|DisplayName|若要在產生的設計工具中顯示裝飾名稱。|圖示裝飾|  
|名稱|裝飾名稱。|IconDecorator|  
|備註|裝飾相關聯的非正式附註。|\<無\>|  
|HorizontalOffset|水平位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|VerticalOffset|垂直位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|OffsetFromLine|從列，相對於它的預設位置，以英吋裝飾的位移。  \(在連接器只。\)|0|  
|OffsetFromShape|相對於它的預設位置，以英吋為單位指定圖案裝飾的位移。  \(在連接器只。\)|0|  
|Position|裝飾的預設位置。|SourceTop|  
  
## TextDecorator  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|DefaultText|要顯示的預設文字。|Label|  
|DisplayName|若要在產生的設計工具中顯示裝飾名稱。|Label|  
|FontSize|裝飾\] 所示之文字的字型大小。|8|  
|FontStyle|裝飾\] 所示的文字字型樣式。|Regular|  
|名稱|裝飾名稱。|Label|  
|備註|裝飾相關聯的非正式附註。|\<無\>|  
|HorizontalOffset|水平位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|VerticalOffset|垂直位移，相對於裝飾，預設位置，以英吋為單位。  \(在圖形僅。\)|0|  
|OffsetFromLine|從列，相對於它的預設位置，以英吋裝飾的位移。  \(在連接器只。\)|0|  
|OffsetFromShape|相對於它的預設位置，以英吋為單位指定圖案裝飾的位移。  \(在連接器只。\)|0|  
|Position|裝飾的預設位置。|TargetBottom|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)