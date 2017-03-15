---
title: "C/C++ 程式碼分析概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma 指示詞, 程式碼分析"
  - "附註, 程式碼分析"
  - "建置整合, 程式碼分析"
  - "C, 程式碼分析"
  - "C/C++ 程式碼分析"
  - "C++, 程式碼分析"
  - "簽入原則, 程式碼分析"
  - "程式碼分析工具"
  - "程式碼分析, C/C++"
  - "命令列, 程式碼分析"
  - "IDE, 程式碼分析"
  - "pragma 指示詞, 程式碼分析"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ 程式碼分析概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C\/C\+\+ 程式碼分析工具會將 C\/C\+\+ 原始程式碼中可能的缺失資訊提供給程式開發人員。  由這個工具所報告的常見程式碼錯誤包括：緩衝區滿溢、未初始化的記憶體、null 指標取值以及記憶體和資源流失。  
  
## IDE \(整合式開發環境\) 整合  
 為了讓程式開發人員可以自然而然地加以使用，分析工具已經完整地整合在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中。  在建置程序期間，針對原始程式碼所產生的警告都會出現在 \[錯誤清單\] 中。  您可以巡覽至造成警告的原始程式碼，而且可以檢視關於原因以及可行解決方法的其他資訊。  
  
## \#pragma 支援  
 程式開發人員可以使用 `#pragma` 指示詞將警告視為錯誤、啟用或停用警告，以及隱藏個別程式碼行的警告。  如需詳細資訊，請參閱[How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/zh-tw/910b8518-71f1-4b2e-b012-70647795642a)。  
  
## 附註支援  
 附註能夠提升程式碼分析的準確性，  因為它們會提供函式參數和傳回值型別之 Pre 和 Post 條件的額外資訊。  如需詳細資訊，請參閱[如何：使用 \_\_analysis\_assume 指定其他程式碼資訊](../Topic/How%20to:%20Specify%20Additional%20Code%20Information%20by%20Using%20__analysis_assume.md)。  
  
## 執行分析工具做為簽入原則的一部分  
 您可能想指定所有的原始程式碼簽入都要滿足特定的原則，  尤其是您會想要確定分析會做為最新本機組建的步驟之一執行。  如需啟用程式碼分析簽入原則的詳細資訊，請參閱[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## Team Build 整合  
 您可以使用建置系統的整合式功能，執行程式碼分析工具做為 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 建置程序的步驟之一。  如需詳細資訊，請參閱[建置應用程式](../Topic/Build%20the%20application.md)。  
  
## 命令列支援  
 除了完全整合在開發環境中之外，程式開發人員也可以從命令列使用分析工具，如以下範例所示：  
  
 `C:\>cl /analyze Sample.cpp`