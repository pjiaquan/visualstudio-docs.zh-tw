---
title: "程式碼分析問題疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 5
---
# 程式碼分析問題疑難排解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題包含下列 Visual Studio 程式碼分析問題的疑難排解資訊。  
  
-   [Visual Studio 2010 規則集中的變更未反映在舊版 Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Visual Studio 2010 規則集中的變更未反映在舊版 Visual Studio  
 當您在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中建立包含子規則集的規則集時，在使用舊版 Visual Studio 的電腦上執行程式碼分析，可能不會套用子規則集的變更。  若要解決這個問題，您必須強制重寫父規則集，也就是包含子規則集的規則集。  
  
1.  在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中開啟父規則集。  
  
2.  進行變更，例如加入或移除規則，然後儲存規則集。  
  
3.  重新開啟規則集，回復變更，然後再次儲存規則集。  
  
## 請參閱  
 [分析應用程式品質](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)