---
title: "如何：為 C/C++ 專案設定程式碼分析屬性 | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "C/C++ 程式碼分析屬性"
  - "程式碼分析屬性"
  - "屬性, C/C++ 程式碼分析"
  - "屬性, 程式碼分析"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：為 C/C++ 專案設定程式碼分析屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在專案的每個組態中設定程式碼分析工具用來分析程式碼的規則。  此外，您也可以引導程式碼分析，使其隱藏由協力廠商工具產生及加入至專案中的程式碼所傳回的警告。  
  
## 程式碼分析屬性頁  
 \[**程式碼分析**\] 屬性頁包含專案所有的程式碼分析組態設定。  若要在 \[**方案總管**\] 中開啟專案的 \[程式碼分析\] 屬性頁，請以滑鼠右鍵按一下專案，然後按一下 \[**屬性**\]。  接下來，展開 \[**組態屬性**\]，再選取 \[**程式碼分析**\] 索引標籤。  
  
## 專案組態和平台  
 \[**組態**\] 清單和 \[**平台**\] 清單可讓您將不同的程式碼分析設定套用到不同的專案組態和平台組合上。  例如，您可以引導程式碼分析將一組規則套用到專案以用於偵錯組建，並套用另一組規則以用於發行的組建 \(Release Build\)。  
  
## 啟用程式碼分析  
 您可以選取 \[**建置時啟用 C\/C\+\+ 的程式碼分析**\]，決定是否要啟用專案的程式碼分析。  您也可以配合 \[**組態**\] 清單使用，好比說您決定對偵錯組建停用程式碼分析並對發行的組建啟用程式碼分析。  
  
 如果專案包含 Managed 程式碼，您可以透過選取 \[**建置時啟用程式碼分析**\]，決定要啟用或停用程式碼分析。  
  
 程式碼分析的目的是要幫助您提升程式碼的品質，以及避免常見的陷阱。  因此，請謹慎考慮是否要停用程式碼分析。  一般來說，比較好的作法是停用您不想套用到專案的規則集或個別規則。  
  
## 產生的程式碼  
 開發人員經常使用工具加快應用程式的開發。  這些工具可能會產生可加入專案中的程式碼。  您可能想查看程式碼分析在產生的程式碼中發現的規則違規。  然而，如果您沒有要維護程式碼，應該不會想要看到這些程式碼。  
  
 \[**一般**\] 屬性頁中的 \[**隱藏所產生程式碼的結果**\] 核取方塊，可讓您選取是否要看到協力廠商工具所產生 Managed 程式碼的程式碼分析警告。  
  
## 規則集  
 如果專案包含 Managed 程式碼，您可以從 \[**執行此規則集**\] 清單選取規則集，藉此選取要在程式碼分析中套用的規則。  
  
## 請參閱  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C\/C\+\+ 程式碼分析警告](../code-quality/code-analysis-for-c-cpp-warnings.md)