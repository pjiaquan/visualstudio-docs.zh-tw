---
title: "堆積配置函式的偵錯版本 | Microsoft Docs"
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
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC 巨集"
  - "_malloc_dbg 函式"
  - "偵錯 [CRT], 堆積配置函式"
  - "偵錯記憶體遺漏, CRT 偵錯程式庫函式"
  - "堆積配置, 偵錯"
  - "malloc 函式"
  - "記憶體遺漏, CRT 偵錯程式庫函式"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 堆積配置函式的偵錯版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C 執行階段程式庫包含堆積配置 \(Heap Allocation\) 函式的特殊偵錯版本。  這些函式的名稱與發行版本相同，再加上「\_dbg」。  本主題以 `malloc` 和 `_malloc_dbg` 為例，說明 CRT 函式發行版本和 \_dbg 版本之間的差異。  
  
 完成 [\_DEBUG](/visual-cpp/c-runtime-library/debug) 定義時，CRT 會將所有的 [malloc](/visual-cpp/c-runtime-library/reference/malloc) 呼叫對應到 [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg)。  因此，您在偵錯時不需要改用 `_malloc_dbg` 取代 `malloc`，來重寫程式碼取得這些功能。  
  
 然而，您可能要明確地呼叫 `_malloc_dbg`。  明確地呼叫 `_malloc_dbg` 會多出下列一些優點：  
  
-   追蹤 `_CLIENT_BLOCK` 類型配置。  
  
-   儲存發生配置要求位置的原始程式檔和行號。  
  
 如果您不要將 `malloc` 呼叫轉換成 `_malloc_dbg`，您可以定義 [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) 來取得原始程式檔資訊，它會造成前置處理器直接將 `malloc` 的所有呼叫對應至 `_malloc_dbg`，而不用依賴 `malloc` 的包裝函式。  
  
 若要追蹤用戶端區塊裡不同類型的配置，您必須直接呼叫 `_malloc_dbg` 並且將 `blockType` 參數設為 `_CLIENT_BLOCK`。  
  
 如果沒有定義 \_DEBUG，`malloc` 呼叫會受到干擾，即 `_malloc_dbg` 呼叫會解析成 `malloc`，[\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) 定義會受到忽略，而無法提供有關配置要求的原始程式檔資訊。  因為 `malloc` 沒有區塊類型參數，`_CLIENT_BLOCK` 類型的要求會被當成標準配置處理。  
  
## 請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)