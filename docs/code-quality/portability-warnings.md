---
title: "可攜性警告 | Microsoft Docs"
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
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "可攜性警告"
  - "Managed 程式碼分析警告，可攜性警告"
  - "警告，可攜性"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 可攜性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可攜性警告會支援各種不同作業系統的可攜性。  
  
## 在本節中  
  
|規則|描述|  
|--------|--------|  
|[CA1900：實值類型欄位應該為可移植的](../code-quality/ca1900-value-type-fields-should-be-portable.md)|這項規則會檢查在 64 位元作業系統上封送處理至 Unmanaged 程式碼時，使用明確配置屬性所宣告的結構是否會正確地對齊。|  
|[CA1901：P\/Invoke 宣告應該是可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|這項規則會評估每個參數的大小和 P\/Invoke 的傳回值，並且在 32 位元和 64 位元作業系統上封送處理至 Unmanaged 程式碼時驗證其大小是否正確。|  
|[CA1903：只使用來自目標架構的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|某一個成員或型別使用的是 Service Pack 中所導入的成員或型別，但是專案的目標 Framework 中卻沒有包含該成員或型別。|