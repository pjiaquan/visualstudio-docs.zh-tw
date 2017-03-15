---
title: "網域類別的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 網域類別"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# 網域類別的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

網域類別具有下列表格中的屬性。  網域類別的詳細資訊，請參閱[了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|存取修飾詞|網域類別的存取層級 \(`public`或`internal`\)。|`public`|  
|自訂屬性|用來將屬性加入至原始檔的程式碼類別從這個網域類別產生。|\<無\>|  
|會產生雙衍生|如果`True`，就會產生部分類別，以便支援透過覆寫的自訂\) 和基底類別。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|具有自訂建構函式|如果`True`，自訂的建構函式將會提供在原始程式碼中。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|`False`|  
|繼承修飾詞|描述一種從網域類別產生的原始檔程式碼類別的繼承 \(`none`， `abstract`或`sealed`\)。|`none`|  
|基底類別|如果這個網域繼承的類別，基底類別的名稱。|\<無\>|  
|名稱|這個網域類別的名稱。|目前的名稱|  
|命名空間|這個網域類別的命名空間。|目前的命名空間|  
|備註|這個網域類別相關聯的非正式附註。|\<無\>|  
|描述|描述用來產生設計工具 UI 的文件。|\<無\>|  
|顯示名稱|將這個網域類別產生的設計工具中顯示的名稱。|\<無\>|  
|說明關鍵字|用於索引 F1 說明這個網域類別選擇性的關鍵字。|\<無\>|  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)