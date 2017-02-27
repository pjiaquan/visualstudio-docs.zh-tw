---
title: "如何：以程式碼分析簽入原則強制程式碼的可維護性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析，簽入原則"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：以程式碼分析簽入原則強制程式碼的可維護性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

開發人員可以使用程式碼度量工具，測量程式碼的複雜度和維護性，但無法叫用程式碼度量做為簽入原則的一部分。  不過，小組可以啟用程式碼分析規則以驗證程式碼是否符合程式碼度量標準，並以簽入原則來強制執行規則。  如需程式碼度量的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。  
  
 開發人員可以啟用繼承深度、類別結合程度、可維護性指數和複雜度規則，以透過程式碼分析簽入原則來強制執行可維護性程式碼。  上述四種規則都可以在程式碼分析原則編輯器的「維護性規則」分類下找到。  
  
 [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] 版本控制的系統管理員可以將程式碼分析的維護性規則加入到簽入原則要求。  這些簽入原則會要求開發人員在初始化簽入之前，先依據這些規則變更執行程式碼分析。  
  
### 若要開啟程式碼分析原則編輯器  
  
1.  在 \[**Team 總管**\] 中，以滑鼠右鍵按一下 Team 專案，按一下 \[**Team 專案設定**\]，然後按一下 \[**原始檔控制**\]。  
  
     \[**原始檔控制**\] 對話方塊隨即出現。  
  
2.  在 \[**簽入原則**\] 索引標籤上，按一下 \[**加入**\]。  
  
     \[**加入簽入原則**\] 對話方塊隨即出現。  
  
3.  選取 \[**簽入原則**\] 清單中的 \[**程式碼分析**\] 核取方塊，然後按一下 \[**確定**\]。  
  
     \[**程式碼分析原則編輯器**\] 對話方塊隨即出現。  
  
### 若要啟用程式碼分析維護性規則  
  
1.  在 \[**程式碼分析原則編輯器**\] 對話方塊的 \[**規則設定**\] 底下，展開 \[**維護性規則**\] 節點。  
  
2.  選取下列規則的核取方塊：  
  
    -   繼承深度：\[**CA1501 AvoidExcessiveInheritance**\] \- 臨界值：深度超過 5 層時發出警告  
  
    -   複雜度：\[**CA1502 AvoidExcessiveComplexity**\] \- 臨界值：超過 25 時發出警告  
  
    -   可維護性指數：\[**CA1505 AvoidUnmaintainableCode**\] \- 臨界值：低於 20 時發出警告  
  
    -   類別結合程度：\[**CA1506 AvoidExcessiveClassCoupling**\] \- 臨界值：類別結合程度超過 80 和方法結合程度超過 30 時發出警告  
  
    -   另外，如果您想在禁止違反規則處進行組建動作，請選取規則描述旁邊的 \[**視警告為錯誤**\] 核取方塊。  
  
3.  按一下 \[**確定**\]。  新的簽入原則就會套用至未來的簽入。  
  
## 請參閱  
 [程式碼度量值](../code-quality/code-metrics-values.md)   
 [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)