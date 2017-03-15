---
title: "程式碼度量值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼度量"
  - "程式碼分析"
  - "測量程式碼品質"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 20
---
# 程式碼度量值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。  只要能夠善用程式碼度量資訊，開發人員便可知道自己應該對哪些型別和\/或方法進行修訂或是更徹底的測試。  此外，開發小組也可以找出潛在的風險、了解專案目前的狀態，並追蹤軟體開發的進度。  
  
## 軟體測量  
 下列清單顯示 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 所計算的程式碼度量資訊結果：  
  
-   **可維護性指數**：算出介於 0 到 100 之間的指數值，代表維護程式碼的相對難易程度。  值愈高表示可維護性愈佳。  色彩編碼分級可用來快速識別程式碼中的問題點。  綠色等級介於 20 和 100 之間，表示程式碼的可維護性良好。  黃色等級介於 10 和 19 之間，表示程式碼的可維護性適中。  紅色等級是介於 0 和 9 之間的等級，表示可維護性低。  
  
-   **循環複雜度**：測量程式碼在結構上的複雜程度。  建立此複雜度的方式是計算程式流程中不同程式碼路徑的數目。  控制流程較為複雜的程式需要執行較多的測試，才能達到正確的程式碼涵蓋範圍，而且比較不容易維護。  
  
    > [!NOTE]
    >  在某些情況下，[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 計算方法循環複雜度的方式與舊版的方式有所不同。  如需詳細資訊，請參閱[程式碼度量問題疑難排解](../code-quality/troubleshooting-code-metrics-issues.md)的＜Visual Studio 2010 程式碼複雜度計算的變更＞一節。  
  
-   **繼承深度**：指出延伸到類別 \(Class\) 階層的根 \(Root\) 的類別定義數目。  階層愈深，可能愈難找出定義與\/或重新定義特定方法和欄位的位置。  
  
-   **類別結合程度**：透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基底型別、介面實作、外部型別上定義的欄位以及屬性修飾等，測量特殊類別的結合程度。  良好的軟體設計應指定聚結性 \(Cohesion\) 高但結合程度 \(Coupling\) 低的型別和方法。  結合程度高表示設計不易重複使用，因為這種設計包含對其他型別的許多相依性。  
  
-   **程式碼行數**：指出程式碼中行數的約略值。  這個數目是以 IL 程式碼為依據，因此不是原始程式碼檔案中精確的行數。  如果數目非常大，表示型別或方法嘗試執行的工作可能過多，而應該分割工作。  這也表示該型別或方法可能難以維護。  
  
## 匿名方法  
 「*匿名方法*」\(Anonymous Method\) 就是沒有名稱的方法。  匿名方法是將程式碼區塊當做委派 \(Delegate\) 參數傳遞時最常使用的方法。  在成員 \(例如方法或存取子\) 中宣告之匿名方法的度量資訊結果都與宣告該方法的成員相關，  但是與呼叫該方法的成員無關。  
  
 如需程式碼度量資訊如何處理匿名方法的詳細資訊，請參閱[匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。  
  
## 產生的程式碼  
 某些軟體工具和編譯器 \(Compiler\) 會產生可加入專案中的程式碼，而且專案開發人員將看不到或是不能變更這些程式碼。  在計算度量資訊值時，程式碼度量資訊通常會忽略產生的程式碼。  以便讓度量資訊值反映開發人員可以查看及變更的內容。  
  
 因為 Windows Form 所產生的程式碼是開發人員可以查看及變更的程式碼，所以不會忽略它。  
  
## 請參閱  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)