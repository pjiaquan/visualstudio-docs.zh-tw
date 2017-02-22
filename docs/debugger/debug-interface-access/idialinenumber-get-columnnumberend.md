---
title: "IDiaLineNumber::get_columnNumberEnd | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumberEnd 方法"
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取一為基礎的來源資料行數的運算式或陳述式的結束處。  
  
## 語法  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的欄號的運算式或陳述式的結束處。  如果值為零，然後資料行結尾資訊不存在。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的資料行值是行中的陳述式的最後一個字元之後的偏移位置在線上的位元組。  
  
## 請參閱  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)