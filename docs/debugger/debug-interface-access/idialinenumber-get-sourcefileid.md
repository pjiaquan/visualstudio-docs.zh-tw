---
title: "IDiaLineNumber::get_sourceFileId | Microsoft Docs"
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
  - "IDiaLineNumber::get_sourceFileId 方法"
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_sourceFileId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取貢獻此行的原始程式檔的唯一來源檔案識別碼。  
  
## 語法  
  
```cpp#  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回提供這一行原始程式檔的唯一來源檔案識別碼。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)