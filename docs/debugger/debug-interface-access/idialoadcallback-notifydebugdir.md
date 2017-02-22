---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback::NotifyDebugDir 方法"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當.exe 檔案中找不到偵錯目錄時，會呼叫它。  
  
## 語法  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### 參數  
 `fExecutable`  
 \[in\]`TRUE`如果偵錯目錄讀取的可執行檔 \(而不是.dbg 檔\)。  
  
 `cbData`  
 \[in\]偵錯目錄中的資料位元組數目。  
  
 `data[]`  
 \[in\]偵錯目錄中填寫的陣列。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回的程式碼通常會被忽略。  
  
## 備註  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法在處理的可執行檔時發現偵錯目錄時，會叫用這個回呼。  
  
 這個方法會移除用戶端進行反向工程的可執行檔和 \(或\) 偵錯的檔案的需求來支援偵錯資訊，而不是在.pdb 檔案中找到。  有了這些資料中，用戶端可以辨識可用的偵錯資訊的型別，及所在的可執行檔或.dbg 檔案中。  
  
 大多數的用戶端並不需要這個回呼，因為`IDiaDataSource::loadDataForExe`方法可無障礙地開啟.pdb 和.dbg 檔案已適時提供服務的符號。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)