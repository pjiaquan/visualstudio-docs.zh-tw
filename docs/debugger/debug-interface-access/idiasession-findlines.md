---
title: "IDiaSession::findLines | Microsoft Docs"
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
  - "IDiaSession::findLines 方法"
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的編譯和來源檔案的識別項內的行號。  
  
## 語法  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `compiland`  
 \[in\][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示編譯。  使用此介面做為內容，以在其中搜尋的行號。  
  
 `file`  
 \[in\][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表原始程式檔，在其中搜尋的行號。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)擷取物件，其中包含一系列的行號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)