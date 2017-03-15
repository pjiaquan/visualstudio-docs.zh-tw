---
title: "CA1308：必須將字串標準化為大寫字母 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308：必須將字串標準化為大寫字母
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 作業會將字串正常化為小寫。  
  
## 規則描述  
 字串應該標準化為大寫字母。  有一小組的字元在轉換成小寫字母時無法達成來回行程。  達成來回行程即代表將字元從一個地區設定轉換為以不同方式表示字元資料的其他地區設定，再從所轉換的字元中正確地擷取原始字元。  
  
## 如何修正違規  
 變更將字串轉換為小寫字母的運算，讓字串改為轉換成大寫字母。  例如，將 `String.ToLower(CultureInfo.InvariantCulture)` 變更為 `String.ToUpper(CultureInfo.InvariantCulture)`。  
  
## 隱藏警告的時機  
 當您不是依據結果進行安全性決策時 \(例如，將結果顯示在 UI 中\)，可以放心地隱藏警告訊息。  
  
## 請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)