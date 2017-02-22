---
title: "適用於 Managed 程式碼的 Managed 最小規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 適用於 Managed 程式碼的 Managed 最小規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這些規則的重點在於程式碼中最關鍵的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。   您應該在您為專案建立的任何自訂規則集中都包含這個規則集。  
  
|規則|描述|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|具有可處置欄位的型別應該是可處置的|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|覆寫 ValueType.Equals 時必須一併多載等號比較運算子|