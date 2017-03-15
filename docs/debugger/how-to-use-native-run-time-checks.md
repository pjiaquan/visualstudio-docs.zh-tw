---
title: "如何：使用原生執行階段檢查 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/O 編譯器選項, /RTC 選項"
  - "/RTC 編譯器選項 [C++], /O 編譯器選項"
  - "陣列 [Visual Studio], 偵錯"
  - "偵錯工具, 原生執行階段檢查"
  - "偵錯工具, 執行階段錯誤"
  - "偵錯陣列"
  - "原生執行階段檢查"
  - "O 編譯器選項, /RTC 選項"
  - "最佳化組建選項"
  - "RTC 編譯器選項, /O 編譯器選項"
  - "執行階段檢查"
  - "執行階段檢查, native"
  - "執行階段錯誤, 偵錯"
  - "執行階段錯誤, 錯誤檢查"
  - "runtime_checks Pragma"
  - "堆疊指標"
  - "堆疊指標, 損毀"
  - "堆疊, 指標損毀"
  - "變數 [偵錯工具], 攔截未初始化區域變數的相依性"
  - "變數 [偵錯工具], 資料遺失"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：使用原生執行階段檢查
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 Visual C\+\+ 中使用原生 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) 來攔截最常見的執行階段錯誤，例如：  
  
-   堆疊指標損壞  
  
-   區域陣列滿溢  
  
-   堆疊損壞  
  
-   未初始化之區域變數的相依性  
  
-   指派至較短變數時流失資料  
  
 如果使用具有最佳化 \(**\/O**\) 組建的 **\/RTC**，便會造成編譯器錯誤。 如果您在最佳化組建中使用 `runtime_checks` Pragma，此 Pragma 會失效。  
  
 如果要偵錯的程式已啟用執行階段錯誤檢查，則當這個程式發生執行階段錯誤時，預設動作是停止和中斷偵錯工具。 您可以變更任何執行階段檢查的這個預設行為。 如需詳細資訊，請參閱[使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 下列程序描述如何在偵錯組建中啟用原生執行階段檢查，以及如何修改原生執行階段檢查行為。  
  
 本節的其他主題提供下列資訊：  
  
-   [自訂使用 C 語言執行階段程式庫的執行階段檢查](../debugger/native-run-time-checks-customization.md)  
  
-   [不使用 C 語言執行階段程式庫進行執行階段檢查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### 在偵錯組建中啟用原生的執行階段檢查  
  
-   使用 **\/RTC** 選項，並與 C 語言執行階段程式庫的偵錯版本建立連結 \(例如 \/MDd\)。  
  
### 修改原生的執行階段檢查行為  
  
-   使用 `runtime_checks` Pragma。  
  
## 請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [執行階段錯誤檢查](/visual-cpp/c-runtime-library/run-time-error-checking)