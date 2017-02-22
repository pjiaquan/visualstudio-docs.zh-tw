---
title: "IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictSystemRootAccess 方法"
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

決定如果搜尋的.pdb 檔案系統的根目錄中。  
  
## 語法  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 任何傳回碼，而非`S_OK`防止搜尋系統根目錄的.pdb 檔案。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)