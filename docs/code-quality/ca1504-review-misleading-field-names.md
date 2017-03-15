---
title: "CA1504：必須檢視可能造成誤導的欄位名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504：必須檢視可能造成誤導的欄位名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|分類|Microsoft.Maintainability|  
|中斷變更|中斷|  
  
## 原因  
 執行個體欄位名稱的開頭為 "s\_"，或是 `static` \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Shared`\) 欄位名稱的開頭為 "m\_"。  
  
## 規則描述  
 許多使用者都會將開頭為 "s\_" 的名稱與靜態資料關聯。  同樣地，開頭為 "m\_" 的欄位名稱則與執行個體 \(成員\) 資料關聯。  為了方便管理程式碼，名稱應該遵循常用的慣例。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用適當的前置字元重新命名欄位。  或者，請加入或移除 `static` 修飾詞，使欄位與目前的後置字元相符。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。