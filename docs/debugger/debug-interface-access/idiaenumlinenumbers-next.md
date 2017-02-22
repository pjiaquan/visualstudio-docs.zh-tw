---
title: "IDiaEnumLineNumbers::Next | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Next 方法"
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定之列舉型別序列中的行號的數字。  
  
## 語法  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### 參數  
 celt  
 \[in\]要擷取列舉值中的行號的數字。  
  
 rgelt  
 \[\] out傳回陣列的[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件，表示您想要的行號。  
  
 pceltFetched  
 \[\] out擷取列舉值中傳回的行號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`是否有沒有更多的行號。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)