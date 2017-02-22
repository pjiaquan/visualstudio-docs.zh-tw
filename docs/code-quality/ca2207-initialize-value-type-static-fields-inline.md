---
title: "CA2207：必須初始化實值類型的靜態欄位內嵌 | Microsoft Docs"
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
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2207：必須初始化實值類型的靜態欄位內嵌
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 實值型別會宣告明確的靜態建構函式。  
  
## 規則描述  
 宣告實值型別時，它會經歷預設的初始設定，所有的實值型別欄位都會設為零，而所有參考型別 \(Reference Type\) 欄位都會設為 `null` \(Visual Basic 中為 `Nothing`\)。  明確的靜態建構函式只保證會在呼叫型別的執行個體建構函式或靜態成員之前執行。  因此，如果未呼叫執行個體建構函式就建立型別，則不保證會執行靜態建構函式。  
  
 如果已初始化所有的靜態資料，而且未宣告明確的靜態建構函式，C\# 編譯器 \(Compiler\) 和 Visual Basic 編譯器就會將 `beforefieldinit` 旗標加入至 MSIL 類別 \(Class\) 定義。  編譯器也會加入包含靜態初始設定程式碼的私用靜態建構函式。  這個私用靜態建構函式保證會在存取型別的任何靜態欄位之前執行。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 相關規則  
 [CA1810：必須初始化參考類型內部的靜態欄位](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)