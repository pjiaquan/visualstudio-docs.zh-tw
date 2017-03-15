---
title: "如何：對方案中的多個專案指定 Managed 程式碼規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：對方案中的多個專案指定 Managed 程式碼規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，方案的所有 Managed 專案都指派了「Microsoft 最小建議規則」程式碼分析「*規則集*」\(Rule Set\)。  您可以在方案的 \[屬性\] 對話方塊中，變更指派至方案中專案的規則集。  
  
> [!NOTE]
>  預設不會將專案程式碼分析當做建置步驟執行。  若要啟用程式碼分析做為建置步驟，請參閱 [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)。  
  
### 若要為 Managed 程式碼方案中的多個專案指定規則集  
  
1.  在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中。  在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] 中開啟方案。  
  
2.  在 \[**分析**\] 功能表上，按一下 \[**為方案設定程式碼分析**\]。  
  
3.  如有需要，展開 \[**通用屬性**\]，然後按一下 \[**程式碼分析設定**\]。  
  
4.  您可以指定一個或多個專案的規則集。  
  
    -   若要為個別專案指定規則集，請按一下專案名稱。  
  
    -   若要為多個專案指定規則集，請按住 CTRL 並按一下各個專案名稱。  
  
    -   若要指定方案中的所有專案，請按住 SHIFT 並按一下專案清單。  
  
5.  按一下專案的 \[**規則集**\] 欄位，然後按一下要套用的規則集名稱。