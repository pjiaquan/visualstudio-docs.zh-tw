---
title: "網域角色的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 9
---
# 網域角色的屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下表中的屬性是與網域角色產生關聯。  網域角色的相關資訊，請參閱[了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)。  如需有關如何使用這些屬性的詳細資訊，請參閱[自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
|屬性|描述|Default|  
|--------|--------|-------------|  
|集合型別|如果這個角色的重數為 0..\* 或 1..\*，這個屬性可自訂的泛型型別用來儲存連結的集合。|`(none)` \- <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> is used|  
|自訂屬性|您在此處指定的屬性會做為屬性加入至產生的程式碼類別。|\<無\>|  
|是屬性的可瀏覽|如果`True`，以及角色 」 屬性如果關聯性的重數是..1 或 1..1，可在使用者瀏覽**屬性**視窗。  屬性會顯示位於關聯性連結的另一端之項目的名稱。|`True`|  
|是屬性產生器|如果`True`，role 屬性會產生這個角色，您可以用來周遊的程式碼中的關聯性。  如果您設定為 false，則您可以藉由網域關聯性的靜態方法來周遊比較沒有效率的方式關聯性。|`True`|  
|屬性 Getter 存取修飾詞|Getter，已產生屬性的存取修飾詞 \(`public`， `internal`， `private`， `protected`，或`protected internal`\)。|`public`|  
|屬性的 set 存取子的存取修飾詞|已產生屬性的 set 存取子的存取修飾詞 \(`public`， `internal`， `private`， `protected`，或`protected internal`\)。|`public`|  
|Multiplicity|可以播放相反角色的模型項目數目 \(`0..1`， `1..1`， `0..*`，或`1..*`\)。  如果多重性為`0..*`或`1..*`，那麼產生的屬性表示集合中。 否則，產生的屬性表示單一模型項目。|關聯性型別而定，以及是否這是關聯中的來源或目標角色。|  
|名稱|網域角色的名稱。  這個屬性不能包含空白字元。|這個角色的角色扮演者的網域類別名稱。|  
|傳播複本|`DoNotPropagateCopy`\-已複製的角色扮演者必須沒有此連結的複本。<br /><br /> `PropagateCopyToLinkOnly`\-已複製的連結會指向現有的相反角色扮演者。<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` \-已複製的連結指向的點相反角色扮演者的複本。|`PropagateCopyToLinkAndOppositeRolePlayer`對於內嵌來源角色。<br /><br /> `DoNotPropagateCopy`其他的角色。<br /><br /> 如需詳細資訊，請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|將刪除傳播|`True`若要刪除的項目，刪除相關的連結時，扮演這個角色。|`True`內嵌的角色目標。<br /><br /> `False`其他的角色。<br /><br /> 如需詳細資訊，請參閱 [自訂刪除行為](../modeling/customizing-deletion-behavior.md)。|  
|屬性名稱|角色扮演者的程式碼中產生的屬性名稱。  這個名稱不能包含空格。|如果這個角色都有一位零相反角色的名稱或一對一的多重性。 否則，pluralized 相反的角色名稱。|  
|角色扮演者|目的網域類別關聯性中扮演這個角色的項目。  這個屬性是唯讀的。|角色扮演者，這個角色的網域類別。|  
|備註|網域角色相關聯的非正式附註。|\<無\>|  
|分類|產生的屬性出現在類別目錄**屬性**產生設計工具中的視窗。  如果這個屬性是空的那麼產生的屬性便會出現在**其他**類別|\<無\>|  
|描述|用於記錄程式碼，而且用在使用者介面，產生的設計工具的描述。<br /><br /> 角色的播放程式類別上已產生屬性的 Intellisense 工具提示中顯示的描述。|`Description for` *角色的完整名稱*|  
|顯示名稱|隨即出現在產生的設計工具中的網域角色的名稱。|Name 屬性調整過的值。|  
|說明關鍵字|選擇性關鍵字用來建立索引的網域角色的 F1 說明。|\<無\>|  
|屬性顯示名稱|產生設計工具產生的角色\] 屬性中所顯示的名稱。|屬性名稱屬性調整過的值。|  
  
> [!NOTE]
>  預設值的顯示名稱根據相關的屬性值，插入每個大寫字元的前面是小寫字元，且不後面跟著另一個大寫字元之前的空格。  
  
## 請參閱  
 [網域關聯性的屬性](../modeling/properties-of-domain-relationships.md)