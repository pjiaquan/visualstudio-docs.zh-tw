---
title: "CA2211：非常數欄位不應該為可見的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2211：非常數欄位不應該為可見的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的靜態欄位既非常數，亦非唯讀。  
  
## 規則描述  
 既非常數，亦非唯讀的靜態欄位不是安全執行緒。  必須小心控制對這類欄位的存取，而且需要進階的程式設計技巧同步 \(Synchronize\) 對類別物件的存取。  因為這些技巧不易學會和精通，而測試這類物件也有困難度，所以最好能用靜態欄位儲存不會變更的資料。  此規則可套用到程式庫，但應用程式不應公開 \(Expose\) 任何欄位。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將靜態欄位設為常數或唯讀。  如果無法這麼做，請將型別重新設計為使用替代機制，例如管理基礎欄位之安全執行緒存取的安全執行緒屬性。  請注意，如鎖定爭用和死結 \(Deadlock\) 這類的問題可能會影響程式庫的效能和行為。  
  
## 隱藏警告的時機  
 如果您正在開發應用程式，因此對包含靜態欄位之型別的存取具有完全控制，則可以放心地隱藏此規則的警告。  使用非常數的靜態欄位會使程式開發人員難以正確使用程式庫，因此程式庫設計工具不應該隱藏此規則的警告。  
  
## 範例  
 下列範例顯示違反此規則的型別。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]