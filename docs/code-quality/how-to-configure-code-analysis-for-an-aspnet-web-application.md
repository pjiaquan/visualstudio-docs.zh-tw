---
title: "如何：設定 ASP.NET Web 應用程式的程式碼分析 | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：設定 ASP.NET Web 應用程式的程式碼分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 和 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] 中，您可以從程式碼分析「*規則集*」\(Rule Set\) 的清單中選取要套用至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的規則集。  預設的規則集：Microsoft 建議的基本規則。  您可以選取另一個規則集以套用至網站。  
  
### 若要設定 ASP.NET 網頁架構專案的規則集  
  
1.  在 \[**方案總管**\] 中選取網站。  
  
2.  在 \[**分析**\] 功能表上，按一下 \[**為網站設定程式碼分析**\]。  
  
3.  如果您已選取方案，而此方案含有一個以上的專案，請從 \[**組態**\] 和 \[**平台**\] 清單中，選取組建組態和目標作業系統。  
  
4.  針對方案中的每個專案，按一下其 \[**規則集**\] 資料行，然後按一下要執行的規則集名稱。  
  
5.  預設會對方案中的所有專案執行程式碼分析。  若要針對特定物件停用或啟用程式碼分析，請遵循下列步驟：  
  
    1.  以滑鼠右鍵按一下專案名稱，然後按一下 \[屬性\]。  
  
    2.  選取或清除 \[**啟用程式碼分析**\] 核取方塊。  您也可以選取 \[**分析**\] 功能表中的 \[**在網站上執行程式碼分析**\]，手動執行程式碼分析。  
  
6.  在 \[**執行此規則集**\] 下拉式清單中，遵循下列步驟：  
  
    -   選取想要使用的規則。  
  
    -   選取 \[**\<瀏覽\>**\] 以指定不在清單中的現有自訂規則集。  
  
    -   定義自訂規則集。  如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。