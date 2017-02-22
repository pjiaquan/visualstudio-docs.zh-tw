---
title: "IDiaSession::findLinesByAddr | Microsoft Docs"
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
  - "IDiaSession::findLinesByAddr 方法"
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取含有指定的位址的行中指定的編譯。  
  
## 語法  
  
```cpp#  
HRESULT findLinesByAddr (   
   DWORD                 seg,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `seg`  
 \[in\]指定特定的地址\] 區段元件。  
  
 `offset`  
 \[in\]指定的特定位址的位移的元件。  
  
 `length`  
 \[in\]指定位址範圍以涵蓋這個查詢使用的位元組的數目。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含一份所有的列數字的封面指定的位址範圍。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 這個範例示範的函式，會取得使用函式的位址及長度的函式中所包含的所有行號。  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,  
                                          IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                seg;  
    DWORD                offset;  
    ULONGLONG            length;  
  
    if (pFunc->get_addressSection ( &seg ) == S_OK &&  
        pFunc->get_addressOffset ( &offset ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## 請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)