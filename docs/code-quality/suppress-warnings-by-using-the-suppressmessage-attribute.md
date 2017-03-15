---
title: "使用 SuppressMessage 屬性隱藏警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCFxCopTool.InputAssemblyFileName"
  - "VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile"
  - "VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression"
  - "VC.Project.VCFxCopTool.OutputFile"
helpviewer_keywords: 
  - "程式碼分析, 來源隱藏"
  - "程式碼分析, SuppressMessage 屬性"
  - "來源隱藏"
  - "SuppressMessage 屬性"
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# 使用 SuppressMessage 屬性隱藏警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指出某個警告不適用，讓小組成員知道程式碼已經過檢閱並且被判定為應該隱藏的警告，通常是很有效的作法。  原始檔中隱藏項目 \(In Source Suppression，ISS\) 可以讓開發人員在接近產生警告的位置放置會隱藏警告的屬性 \(Attribute\)。  您可以直接將 ISS 屬性加入到原始程式檔，也可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中的捷徑功能表。  
  
## 在本節中  
  
|||  
|-|-|  
|[原始檔中隱藏項目概觀](../code-quality/in-source-suppression-overview.md)|了解 ISS 以及如何在程式碼中使用它。|  
|[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|了解如何使用捷徑功能表來隱藏 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中的警告。|  
  
## 相關章節  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)