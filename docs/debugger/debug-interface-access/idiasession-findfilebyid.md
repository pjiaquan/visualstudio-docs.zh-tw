---
title: "IDiaSession::findFileById | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findFileById 方法"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

藉由原始程式檔來擷取來源檔案的識別項。  
  
## 語法  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### 參數  
 `uniqueId`  
 \[in\]指定的來源檔案的識別項。  
  
 `ppResult`  
 \[\] out傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)擷取物件，代表原始程式檔。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 來源檔案的識別項是唯一的值，以使所有的原始程式檔是唯一在內部用來 DIA SDK。  這個方法通常會在內部將 DIA SDK。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)