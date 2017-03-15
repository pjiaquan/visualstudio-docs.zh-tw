---
title: "程式碼分析規則集參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析，規則集"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 43
---
# 程式碼分析規則集參考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您為 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 、 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] 中的 Managed 程式碼專案設定程式碼分析時，會出現內建*rule sets* 的清單。  您可以使用其中一個 standar 規則集，也可以自訂規則集以符合您的專案需求。  
  
## 可用的規則集  
 下表列出預設的規則集:  
  
|||  
|-|-|  
|[所有規則規則集](../code-quality/all-rules-rule-set.md)|這個規則集包含所有規則。  執行這個規則集可能導致大量的警告回報。  使用這個規則集可讓您對程式碼中的所有問題有全面性的了解。  這可以幫助您決定哪些焦點更為集中的規則集最適合用來執行您的專案。|  
|[適用於 Managed 程式碼的基本正確性規則規則集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|這些規則的重點在於使用 Framework 應用程式開發介面時發生的邏輯錯誤和常見錯誤。  包含這個規則集可將最小建議規則所回報的警告清單加以擴大。|  
|[適用於 Managed 程式碼的基本設計方針規則規則集](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|這些規則的重點在於強制最佳實務作法，使程式碼易懂又好用。  如果專案包含程式庫程式碼或您想強制最佳實務以便於維護程式碼，請包含這個規則集。|  
|[適用於 Managed 程式碼的擴充正確性規則規則集](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|這些規則會擴大基本正確性規則的範圍，讓回報的邏輯和 Framework 使用錯誤達到最大的功效。  另外則特別強調 COM Interop 和行動應用一類特定案例。  如果這些案例適合您的專案或您想找出專案的其他問題，請考慮包含這個規則集。|  
|[適用於 Managed 程式碼的擴充設計方針規則規則集](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|這些規則會擴大基本設計方針規則的範圍，讓回報的使用和維護性問題達到最大的功效。  另外還強調命名方針。  如果您的專案包含程式庫程式碼或您想強制最高標準來撰寫容易維護的程式碼，請考慮包含這個規則集。|  
|[適用於 Managed 程式碼的全球化規則規則集](../code-quality/globalization-rules-rule-set-for-managed-code.md)|這些規則的重點在於處理導致應用程式中的資料用在不同語言、當地語系和文件特性時會無法正確顯示的問題。  如果應用程式已當地語系化或全球化，請包含這個規則集。|  
|[適用於 Managed 程式碼的 Managed 最小規則規則集](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼中最關鍵的問題，可用來找出最精確的程式碼分析。這些規則數目小且僅供在有限的 Visual Studio 版本中執行。請搭配其他 Visual Studio 版本使用 MinimumRecommendedRules.ruleset。|  
|[適用於 Managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|這些規則的重點在於程式碼中最關鍵的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。  您應該在您為專案建立的任何自訂規則集中都包含這個規則集。|  
|[混合最小規則規則集](../code-quality/mixed-minimum-rules-rule-set.md)|這些規則的重點在於支援 Common Language Runtime 之 C\+\+ 專案中最關鍵的問題，包括潛在的安全性漏洞和應用程式損毀。  您應該在您為支援 Common Language Runtime 之 C\+\+ 專案建立的任何自訂規則集中都包含這個規則集。|  
|[混合建議規則規則集](../code-quality/mixed-recommended-rules-rule-set.md)|這些規則的重點在於支援 Common Language Runtime 之 C\+\+ 專案中最常見且關鍵的問題，包括潛在的安全性漏洞和應用程式損毀，以及其他重要邏輯和設計錯誤。  您應該在您為支援 Common Language Runtime 之 C\+\+ 專案建立的任何自訂規則集中都包含這個規則集。這個規則集是設計用來與 Visual Studio Professional \(含\) 以上版本一起設定。|  
|[原生最小規則規則集](../code-quality/native-minimum-rules-rule-set.md)|這些規則的重點在於機器碼中最關鍵的問題，包括潛在的安全性漏洞和應用程式損毀。  您應該在您為原生專案建立的任何自訂規則集中都包含這個規則集。|  
|[原生建議規則規則集](../code-quality/native-recommended-rules-rule-set.md)|這些規則的重點在於機器碼中最關鍵且常見的問題，包括潛在的安全性漏洞和應用程式損毀。您應該在您為原生專案建立的任何自訂規則集中都包含這個規則集。這個規則集是設計用來與 Visual Studio Professional \(含\) 以上版本搭配使用。|  
|[適用於 Managed 程式碼的安全性規則規則集](../code-quality/security-rules-rule-set-for-managed-code.md)|這個規則集包含所有 Microsoft 安全性規則。  包含這個規則集可讓回報的潛在安全性威脅數目達到最大。|