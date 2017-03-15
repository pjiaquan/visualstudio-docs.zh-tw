---
title: "如何：在程式碼剖析工具報告檢視中設定減少雜訊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "程式碼剖析工具，修剪"
  - "程式碼剖析工具，報告干擾降低"
  - "程式碼剖析工具，摺疊"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在程式碼剖析工具報告檢視中設定減少雜訊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以透過限制 \[呼叫樹狀圖\] 檢視和 \[配置\] 檢視中顯示的資料量，以設定效能報告來減少雜訊。  使用雜訊削減時，效能問題將更為顯著，  這對於分析效能報告是很有幫助的。  
  
 雜訊削減組態選項包括下列設定：  
  
-   **修剪**：分析報告時，檢視將會省略落在您所設定之值和臨界值設定內的函式，如後面的修剪程序所述。  根據預設，系統會啟用修剪。  
  
-   **摺疊**：若啟用摺疊，在符合您所指定之設定的路徑上，所有的連續函式都會合併，如後面的摺疊程序所述。  根據預設，系統會啟用摺疊。  
  
### 若要設定效能報告的修剪功能  
  
1.  當產生的報告中顯示 \[呼叫樹狀圖\] 檢視或 \[配置\] 檢視時，在 \[**程式開發人員**\] 功能表中，按一下 \[**分析工具**\]，再按一下 \[**減少雜訊選項**\]。  
  
     \[**雜訊削減**\] 對話方塊隨即出現。  
  
2.  若要啟用修剪，請依照下列步驟執行：  
  
    1.  選取 \[**啟用修剪**\]。  這是預設值。  
  
        > [!NOTE]
        >  如果已啟用雜訊削減，報告中將會顯示資訊列。  如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)與[配置檢視](../profiling/dotnet-memory-allocations-view.md)。  
  
    2.  使用 \[**值**\] 下拉式清單，並選擇適用的設定，藉以設定值的設定。  
  
    3.  在 \[**臨界值**\] 文字方塊中輸入百分比值，以設定需要的臨界值設定。  
  
    4.  若要在產生的報告中啟用雜訊削減警告，請選取 \[**啟用雜訊削減時顯示警告**\]。  這是預設值。  
  
3.  若要停用修剪，請清除 \[**啟用修剪**\]。  
  
4.  按一下 \[**確定**\]。  
  
### 若要設定效能報告的摺疊功能  
  
1.  在 \[**程式開發人員**\] 功能表中，按一下 \[**分析工具**\]，然後按一下 \[**雜訊削減選項**\]。  
  
     \[**雜訊削減**\] 對話方塊隨即出現。  
  
2.  若要啟用摺疊，請依照下列步驟執行：  
  
    1.  選取 \[**啟用摺疊**\]。  這是預設值。  
  
        > [!NOTE]
        >  如果已啟用雜訊削減，報告中將會顯示資訊列。  如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)與[配置檢視](../profiling/dotnet-memory-allocations-view.md)。  
  
    2.  使用 \[**值**\] 下拉式清單，並選取適用的設定，藉以設定值的設定。  
  
    3.  在 \[**臨界值**\] 文字方塊中輸入百分比值，以設定需要的臨界值設定。  
  
    4.  若要在產生的報告中啟用雜訊削減警告，請選取 \[**啟用雜訊削減時顯示警告**\]。  這是預設值。  
  
3.  若要停用摺疊，請清除 \[**啟用摺疊**\]。  
  
4.  按一下 \[**確定**\]。  
  
## 請參閱  
 [自訂程式碼剖析工具報表檢視](../profiling/customizing-performance-tools-report-views.md)   
 [如何：從檢測排除或包含 Short 函式](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)   
 [呼叫樹狀圖檢視](../profiling/call-tree-view.md)   
 [配置檢視](../profiling/dotnet-memory-allocations-view.md)