---
title: "CA1814：建議使用不規則陣列取代多維陣列 | Microsoft Docs"
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
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1814：建議使用不規則陣列取代多維陣列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|分類|Microsoft.Performance|  
|中斷變更|中斷|  
  
## 原因  
 成員被宣告為多維陣列。  
  
## 規則描述  
 不規則陣列是一種陣列，其元素也是陣列。  組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將多維陣列變更為不規則陣列。  
  
## 隱藏警告的時機  
 如果必須符合 CLS 標準或多維陣列不會浪費空間，則您可以隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示不規則陣列和多維陣列的宣告。  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]