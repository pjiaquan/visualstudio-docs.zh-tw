---
title: "用戶端區塊攔截函式 | Microsoft Docs"
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
  - "_CrtSetDumpClient 函式"
  - "用戶端區塊, 攔截函式"
  - "用戶端區塊, 驗證和報告資料"
  - "偵錯 [C++], 攔截函式"
  - "攔截, 用戶端區塊"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 用戶端區塊攔截函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您要驗證或報告儲存在 `_CLIENT_BLOCK` 區塊裡的資料內容，您可以撰寫符合這個目的的函式。  您所撰寫的函式，必須與下列在 CRTDBG.H 裡定義的原型類似：  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 換句話說，攔截函式應該接受配置區塊一開頭的 **void** 指標，以及表示配置大小的 **size\_t** 型別值，並且傳回 `void`。  除此之外，其他的內容則由您決定。  
  
 一旦您使用 [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) 來安裝攔截函式，每一次 `_CLIENT_BLOCK` 區塊傾印時都會呼叫它。  然後您可以使用 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) 來取得傾印區塊的類型或子類型的資訊。  
  
 您傳入 `_CrtSetDumpClient` 的函式指標是定義在 CRTDBG.H 裡的 **\_CRT\_DUMP\_CLIENT** 類型：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## 請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/zh-tw/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)