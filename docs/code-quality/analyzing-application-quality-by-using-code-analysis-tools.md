---
title: "使用程式碼分析工具進行應用程式品質分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.analysisresults"
helpviewer_keywords: 
  - "應用程式品質, 分析"
  - "程式碼分析"
  - "小組開發, 分析應用程式品質"
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# 使用程式碼分析工具進行應用程式品質分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 本章節內容  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 Managed 程式碼的 Visual Studio 程式碼分析會提供 Managed 組件的相關資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。  警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。  
  
 [分析 C\/C\+\+ 程式碼品質](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 C\/C\+\+ 程式碼分析工具會將其 C\/C\+\+ 原始程式碼中可能的缺失相關資訊提供給開發人員。  這個工具所報告的常見程式碼撰寫錯誤包括緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體和資源流失。  
  
 [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 選取和建立要套用至您的專案的「*規則集*」。  
  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)  
 修正程式碼分析功能中的錯誤。  
  
 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 當您使用 Team Foundation 版本控制 \(TFVC\) 時，您可以針對 Team 專案建立簽入原則，該原則會強制執行做法，導致更好的程式碼和更有效率的群組開發。  簽入原則是在 Team 專案層級設定的規則，而且會在允許程式碼簽入之前，於開發人員電腦上強制執行。  
  
### 驅動程式程式碼分析  
 程式碼分析工具可以協助改進您的驅動程式的穩定性和可靠性，方法是有系統地分析驅動程式原始程式碼。  
  
 [使用程式碼分析工具進行驅動程式品質分析](http://go.microsoft.com/fwlink/?LinkId=227618)  
 驅動程式的程式碼分析是一個編譯時期靜態驗證工具，會偵測 C 和 C\+\+ 程式中的基本程式碼錯誤，並包含特殊模組，它是設計用來 \(主要\) 偵測核心模式驅動程式碼中的錯誤..  靜態驅動程式驗證器 \(SDV\) 是一種靜態驗證工具，有系統地分析 Windows 核心模式驅動程式的原始程式碼。  SDV 會判斷驅動程式是否正確地與 Windows 作業系統核心互動。  
  
 [驅動程式程式碼分析警告](http://go.microsoft.com/fwlink/?LinkId=225920)  
 描述驅動程式之程式碼分析在偵測到驅動程式程式碼中可能阿生的錯誤時，所報告的警告。  
  
## 相關工作  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 在這裡插入說明。  
  
 [對程式碼進行單元測試](../test/unit-test-your-code.md)  
 在這裡插入說明。