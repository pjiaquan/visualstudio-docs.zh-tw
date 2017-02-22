---
title: "IDiaLineNumber::get_columnNumber | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumber 方法"
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取運算式或陳述式的開始處的資料行數目。  
  
## 語法  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的欄號的運算式或陳述式的開始處。  如果值為零，則無法存在於資料行資訊。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 這個方法傳回的資料行的值是線與列中的陳述式的第一個字元位元位移。  
  
## 請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)