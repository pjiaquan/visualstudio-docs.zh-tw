---
title: "如何：在機器碼中設定執行緒名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [C++], 執行緒"
  - "偵錯 [Visual Studio], 執行緒"
  - "SetThreadName 函式"
  - "執行緒名稱"
  - "執行緒處理 [Visual Studio], 名稱"
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：在機器碼中設定執行緒名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要在程式中設定執行緒名稱，請如下列程式碼範例所示，使用 `SetThreadName` 函式。 請注意，執行緒名稱會複製到執行緒，以便釋放 `threadName` 參數的記憶體。  
  
## 範例  
  
```cpp  
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
  
```  
  
## 請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)