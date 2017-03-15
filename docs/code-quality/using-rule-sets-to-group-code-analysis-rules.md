---
title: "使用規則集分組程式碼分析規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "程式碼分析, 規則集"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 36
---
# 使用規則集分組程式碼分析規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]中設定程式碼分析時，可以從 Microsoft 內建*規則集* 清單中選擇。  規則集是程式碼分析規則的邏輯群組，可識別目標問題及特定的條件。  例如，您可以套用專為掃描公用應用程式開發介面的程式碼所設計的規則集，或者套用只包含最小建議規則的規則集。  您也可以套用包含所有規則的規則集。  
  
 您可以加入或刪除規則以自訂規則集，或是變更規則以顯示在 \[**錯誤清單**\] 視窗中做為警告或錯誤。  自訂規則集可以滿足您對特定開發環境的需求。  當您自訂規則集時，規則集頁面會提供搜尋及篩選工具，在過程中協助您。  
  
## 一般工作  
  
|工作|相關內容|  
|--------|----------|  
|**獲得實務練習**：使用程式碼分析工具指定自訂規則集，以便在簡單的 .NET Framework 應用程式中尋找和修正問題。|-   [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**設定專案的程式碼分析**：為專案、網站或方案，選擇現有的規則集。|-   [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用規則集指定要執行的 C\+\+ 規則](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何：對方案中的多個專案指定規則集](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**自訂規則集**：指定要套用至專案的規則。|-   [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**了解內建規則集**：檢視組成內建規則集的程式碼分析規則。|-   [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)|  
|**整合程式碼分析與 Team Foundation Server**：[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 簽入原則可讓開發小組確認，所有程式碼的簽入都符合一組通用的程式碼分析標準。|-   [如何：同步處理具有 Team 專案簽入原則的程式碼專案規則集](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|