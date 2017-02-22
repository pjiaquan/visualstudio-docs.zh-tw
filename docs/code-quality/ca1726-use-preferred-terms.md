---
title: "CA1726：建議使用慣用詞彙 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726：建議使用慣用詞彙
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UsePreferredTerms|  
|CheckId|CA1726|  
|分類|Microsoft.Naming|  
|中斷變更|中斷 \- 在組件 \(Assembly\) 上引發時<br /><br /> 非中斷 \- 在型別參數上引發時|  
  
## 原因  
 外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。  或者該名稱包含 Flag 或 Flags 一詞。  
  
## 規則描述  
 這個規則會將識別項剖析為語彙基元 \(Token\)。  每個單一語彙基元和每個連續的雙重語彙基元組合，都會與規則內建詞彙以及任何自訂字典之 Deprecated 區段中的詞彙進行比較。  下表會顯示建置到規則中之詞彙及其慣用的替代詞彙。  
  
|過時的詞彙|慣用的詞彙|  
|-----------|-----------|  
|Arent|AreNot|  
|已取消|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag 或 Flags|沒有取代詞彙。  不要使用。|  
|Hadnt|HadNot|  
|Hasn’t|HasNot|  
|Havent|HaveNot|  
|Indices|索引|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## 如何修正違規  
 若要修正此規則的違規情形，請以慣用的替代詞彙取代該詞彙。  
  
## 隱藏警告的時機  
 如果識別項的名稱是有意的，並且特別與原始詞彙而不是與慣用詞彙相關聯時，則隱藏這項規則的警告。  
  
## 相關規則  
 [命名警告](../code-quality/naming-warnings.md)