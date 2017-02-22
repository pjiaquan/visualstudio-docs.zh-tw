---
title: "IDiaSession::findLinesByVA | Microsoft Docs"
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
  - "IDiaSession::findLinesByVA 方法"
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的虛擬位址 \(VA\) 範圍內包含的行的行號資訊。  
  
## 語法  
  
```cpp#  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `va`  
 \[in\]指定的位址為 VA.  
  
 `length`  
 \[in\]指定位址範圍以涵蓋這個查詢使用的位元組的數目。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含一份所有的列數字的封面指定的位址範圍。  
  
## 範例  
 這個範例示範的函式，會取得使用函式的虛擬位址及長度的函式中所包含的所有行號。  
  
```cpp#  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## 請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)