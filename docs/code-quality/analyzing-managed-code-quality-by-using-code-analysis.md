---
title: "使用程式碼分析進行 Managed 程式碼品質分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析，Managed 程式碼"
  - "Managed 程式碼分析"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用程式碼分析進行 Managed 程式碼品質分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用Visual Studio的程式碼分析，找出程式碼中的潛在問題，例如不安全的資料存取、使用情況違規，以及設計問題。  程式碼分析適用於 .NET Framework、原生 \(C 和 C\+\+\) 和資料庫應用程式。  Managed 程式碼的程式碼分析會組織以特定編碼問題為目標的「*規則集*」\(Rule Set\) 中的規則。  
  
## 一般工作  
  
|一般工作|支援內容|  
|----------|----------|  
|**獲得實務練習**：透過修正簡單 .NET Framework 應用程式中的缺失，了解程式碼分析的基本概念。|-   [逐步解說：分析 Managed 程式碼中的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**設定專案的程式碼分析**：Managed 程式碼的規則會組成為規則集，並且以特定方面 \(例如安全性或設計\) 為目標。  您可以使用其中一個 Microsoft 標準規則集或建立自己的規則集。|-   [Managed 程式碼的程式碼分析概觀](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**執行程式碼分析**：您可以指定要在每次建置專案組態時自動執行的程式碼分析，也可以在專案上手動執行程式碼分析。|-   [如何：啟用和停用自動程式碼分析](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)<br />-   [如何：手動執行程式碼分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**分析程式碼分析的結果**: 程式碼分析警告和錯誤會列在\[錯誤清單\]視窗中。  您可以選取警告或錯誤標題顯示警告的其他資訊以顯示和反白引發規則的原始程式碼行。  您可以選取警告 ID 以在 MSDN Library 中顯示詳細資訊 \(包括如何解決此問題的資訊和範例\)。|-   [如何：檢視 Managed 程式碼的缺失](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Managed 程式碼的程式碼分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [依據 CheckId 列出警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**整合程式碼分析與開發生命週期**：[!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]中的簽入原則可讓開發小組確認，所有程式碼的簽入都符合一組通用的程式碼分析標準。  建立程式碼分析規則違規的工作項目是一項簡單的程序，可以在 \[錯誤清單\] 視窗中執行。|-   [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何：同步處理具有 Team 專案簽入原則的程式碼專案規則集](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何：為 Managed 程式碼的缺失建立工作項目](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|