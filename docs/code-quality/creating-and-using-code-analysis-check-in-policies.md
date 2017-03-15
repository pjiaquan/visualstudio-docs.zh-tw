---
title: "建立和使用程式碼分析簽入原則 | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析, 簽入原則"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 建立和使用程式碼分析簽入原則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您使用 Team Foundation 版本控制 \(TFVC\) 時，可以針對 Team 專案中的 .NET Framework 和原生 \(C\/C\+\+\) 程式碼專案建立程式碼分析簽入原則。  您可以使用程式碼分析簽入原則，來控制及改善簽入至程式碼基底的程式碼品質。  
  
 當本機組建是最新版，而且已經對最新原始程式檔執行程式碼分析時，便可通過此原則。  在程式碼專案中啟用的程式碼分析規則至少必須包含 Team 專案簽入原則中所定義的相同規則。  \[Team 專案設定\] 中指定為錯誤的規則，在程式碼專案中也必須指定為錯誤。  
  
> [!IMPORTANT]
>  程式碼分析簽入原則不適用於網站專案。  它們可以套用到 Web 應用程式專案。  
  
 您可以使用 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]的 \[Team 專案設定\] 建立程式碼分析簽入原則。  簽入原則是針對 Team 專案指定並強制執行，但是程式碼分析執行則是針對本機開發電腦上的個別程式碼專案而設定及執行的。  本節描述如何指定 Team 專案的程式碼分析簽入原則，以及如何實作 Managed 程式碼的自訂程式碼分析原則。  
  
## 在本節中  
 [如何：建立或更新標準程式碼分析簽入原則](../Topic/How%20to:%20Create%20or%20Update%20Standard%20Code%20Analysis%20Check-in%20Policies.md)  
 說明用來設定及修改 Team 專案程式碼分析原則的步驟。  
  
 [為 Managed 程式碼實作自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 說明用來建立 Team 專案簽入原則自訂規則集，以及同步處理 Team 專案的程式碼專案與簽入原則的步驟。  
  
 [程式碼分析簽入原則的版本相容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 說明 [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)] 版本之間的程式碼分析簽入相容性問題。  
  
 [如何：自訂程式碼分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
 說明如何將字組和語彙基元加入至程式碼分析命名規則中所參考的字典。  
  
## 相關章節  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)