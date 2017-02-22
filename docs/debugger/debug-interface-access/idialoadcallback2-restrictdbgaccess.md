---
title: "IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictDBGAccess 方法"
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictDBGAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

決定如果尋找偵錯資訊是從.dbg 的檔案。  
  
## 語法  
  
```cpp#  
HRESULT RestrictDBGAccess();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 任何傳回值，而非`S_OK`防止尋找.dbg 檔案中的偵錯資訊。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)