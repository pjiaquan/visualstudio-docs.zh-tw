---
title: "只有使用 Microsoft .NET Framework 2.0 或 3.0 版本時才支援混合模式偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 只有使用 Microsoft .NET Framework 2.0 或 3.0 版本時才支援混合模式偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 2.0 版之前的 Microsoft .NET Framework 沒有提供 64 位元處理序的混合模式偵錯支援。  這表示在偵錯時，您無法從 Managed 程式碼逐步執行到機器碼，或從機器碼逐步執行到 Managed 程式碼。  
  
 若要解決這個問題，您可以：  
  
-   更新專案，以使用 Microsoft .NET Framework 2.0 或 3.0。  
  
-   在不同的偵錯工作階段中分別偵錯 Managed 程式碼和機器碼。  
  
-   將混合程式碼當做 32 位元處理序來偵錯，如下列程序所述。  
  
### 若要將作業系統變更為 32 位元 \(Visual Basic 或 C\#\)  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，然後按一下捷徑功能表中的 \[**屬性**\]。  
  
2.  在屬性頁中，按一下 \[**編譯**\] 或 \[**偵錯**\] 索引標籤。  
  
3.  按一下 \[**平台**\]，然後從平台清單選取 \[**x86**\]。  
  
     根據預設，Visual Basic 和 C\# 編譯器會產生可針對任何 CPU 執行的程式碼。  在 64 位元電腦上，這些二進位檔會當做 64 位元處理序執行。  若要在 32 位元處理序上執行，您必須選擇 \[**Win32**\]，而非 \[**AnyCPU**\]。  
  
### 若要將作業系統變更為 32 位元 \(C\/C\+\+\)  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，然後按一下捷徑功能表中的 \[**屬性**\]。  
  
     在屬性頁中，按一下 \[**平台**\]，然後從平台清單選取 \[**Win32**\]。  
  
### 若要更正這個錯誤  
  
-   請參閱[Setting Up SQL Debugging](http://msdn.microsoft.com/zh-tw/3db09e68-edcc-42de-9c22-4e97cfd55ab3)。  
  
## 請參閱  
 [偵錯 64 位元應用程式](../debugger/debug-64-bit-applications.md)