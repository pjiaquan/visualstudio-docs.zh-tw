---
title: "Managed 程式碼的程式碼分析概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "程式碼分析，Managed 程式碼"
  - "Managed 程式碼，程式碼分析"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Managed 程式碼的程式碼分析概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Managed 程式碼的程式碼分析可以分析 Managed 組件並回報有關組件的資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。  
  
 分析工具會將分析期間所做的檢查顯示為警告訊息。  警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。  
  
## IDE \(整合式開發環境\) 整合  
 開發人員可以對專案自動執行程式碼分析，或者也可以手動執行分析。  
  
 若要每次建置專案時都執行程式碼分析，請在專案的屬性頁上選取 \[**建置時啟用程式碼分析 \(定義 CODE\_ANALYSIS 常數\)**\]。  如需詳細資訊，請參閱 [如何：啟用和停用自動程式碼分析](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)。  
  
 若要在專案上手動執行程式碼分析，請按一下 \[**分析**\] 功能表上的 \[**針對 *ProjectName* 執行程式碼分析**\]。  如需詳細資訊，請參閱 [如何：啟用和停用自動程式碼分析](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)。  
  
## 規則集  
 Managed 程式碼的程式碼分析規則會組成「*規則集*」\(Rule Set\)。  您可以使用其中一個 Microsoft 標準規則集，或建立自訂規則集來滿足特定需求。  如需詳細資訊，請參閱[使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)。  
  
## 原始檔中隱藏項目  
 最大的用途是指出某個警告不適用。  這會通知程式開發人員和其他稍後可能會檢閱程式碼的人員，指出您已經調查此警告並且隱藏或忽略它。  
  
 警告的「原始檔中隱藏項目」是透過自訂屬性來實作。  若要隱藏警告，請將 `SuppressMessage` 屬性加入至原始程式碼，如下列範例所示：  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 如需詳細資訊，請參閱[使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
## 執行程式碼分析做為簽入原則的一部分  
 從組織的角度來看，您可能想指定所有的簽入都要滿足特定的原則，  尤其您會想要確認您已經確實遵循這些原則：  
  
-   所簽入的程式碼中沒有建置錯誤。  
  
-   已執行程式碼分析做為最新組建的一部分。  
  
 您可以指定簽入原則，達成上述要求。  如需詳細資訊，請參閱[使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)。  
  
## Team Build 整合  
 您可以使用建置系統的整合式功能，執行分析工具做為建置流程的一部分。  如需詳細資訊，請參閱[建置應用程式](../Topic/Build%20the%20application.md)。  
  
## 請參閱  
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [如何：啟用和停用自動程式碼分析](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)