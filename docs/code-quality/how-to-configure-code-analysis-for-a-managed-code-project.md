---
title: "如何：設定 Managed 程式碼專案的程式碼分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "程式碼分析，選取規則集"
  - "程式碼分析，規則集"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：設定 Managed 程式碼專案的程式碼分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 和 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]，您可以從程式碼分析的清單中選取 *規則集* 以應用於一個管理的程式專案。  預設的規則集是「Microsoft 最小建議規則」。  您可以套用其他規則集至某一個專案，或是套用至方案中的所有專案。  
  
> [!NOTE]
>  如需如何設定 ASP.NET Web 應用程式之規則集的詳細資訊，請參閱 [如何：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。  
  
### 若要設定 .NET Framework 專案的規則集  
  
1.  在 \[**方案總管**\] 中按一下專案。  
  
2.  在 \[**分析**\] 功能表上，按一下 \[**Configure Code Analysis for** *ProjectName*\]。  
  
3.  在 \[**組態**\] 和 \[**平台**\] 清單中，按一下組建組態和目標平台。  
  
4.  若要在每一次使用選取的組態建置專案時執行程式碼分析，請選取 \[**建置時啟用程式碼分析 \(定義 CODE\_ANALYSIS 常數\)**\] 核取方塊。  您也可以開啟 \[**分析**\] 功能表並按一下 \[**針對 *ProjectName* 執行程式碼分析**\]，手動執行程式碼分析。  
  
5.  根據預設，由外部工具所自動產生的程式碼，程式碼分析不會報告警告。  若要檢視所產生程式碼中的警告，請清除 \[**隱藏所產生程式碼的結果**\] 核取方塊。  
  
    > [!NOTE]
    >  表單和範本中出現錯誤和警告時，這個選項不會隱藏所產生程式碼的程式碼分析錯誤和警告。  您可以同時檢視及維護表單或範本的原始程式碼。  
  
6.  在 \[**執行此規則集**\] 清單中，執行下列其中一項操作：  
  
    -   按一下您要使用的規則集。  
  
    -   按一下 \[**\<瀏覽...\>**\] 以指定不在清單中的現有自訂規則集。  
  
    -   定義自訂規則集。  
  
         如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。  
  
## 請參閱  
 [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)