---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictOriginalPathAccess 方法"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

決定是否要尋找.pdb 檔原始的偵錯目錄中。  
  
## 語法  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 任何傳回碼，而非`S_OK`防止尋找.pdb 檔案在原始的偵錯目錄中。  原始的偵錯目錄是編譯為可執行檔中，執行時偵錯符號檔的路徑。  這個路徑不一定是可執行檔所在的路徑相同。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)