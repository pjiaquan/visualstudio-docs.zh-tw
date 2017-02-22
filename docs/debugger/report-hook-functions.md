---
title: "報告攔截函式 | Microsoft Docs"
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
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport 函式"
  - "_CrtSetReportHook 函式"
  - "偵錯工具, 報告攔截函式"
  - "偵錯 [C++], 攔截函式"
  - "攔截, 報告"
  - "記憶體配置, 偵錯堆積"
  - "報告攔截函式"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 報告攔截函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

報告攔截函式，使用 [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook) 安裝，會在每次 [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) 產生偵錯報告時呼叫。  除此之外，您可以使用它來篩選報告以專注於特定類型的配置。  報告攔截函式應該有像下列的原型：  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 您傳入至 **\_CrtSetReportHook**  的指標是在 CRTDBG.H 裡 **\_CRT\_REPORT\_HOOK** 定義的類型：  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 當執行階段程式庫呼叫攔截函式時，*nRptType* 引數包含報告的分類 \(**\_CRT\_WARN**、**\_CRT\_ERROR** 或 **\_CRT\_ASSERT**\)，*szMsg* 包含完整重組報告訊息字串的指標，而 *retVal* 指定 `_CrtDbgReport` 是否應該在產生報告或啟動偵錯工具繼續照常執行 \(*retVal* 值為零時會繼續執行，值為 1 時會啟動偵錯工具\)。  
  
 如果攔截能完整處理該訊息，而不需要進一步的報告，它應該就會傳回 **TRUE**。  如果它傳回的是 **FALSE**，`_CrtDbgReport` 會以一般方式報告訊息。  
  
## 請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/zh-tw/21e1346a-6a17-4f57-b275-c76813089167)