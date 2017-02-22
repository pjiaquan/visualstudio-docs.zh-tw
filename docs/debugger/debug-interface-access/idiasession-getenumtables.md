---
title: "IDiaSession::getEnumTables | Microsoft Docs"
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
  - "IDiaSession::getEnumTables 方法"
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::getEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取包含在符號存放區中的所有資料表的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT getEnumTables (   
   IDiaEnumTables** ppEnumTables  
);  
```  
  
#### 參數  
 `ppEnumTables`  
 \[\] out傳回[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)物件。  您可以使用這個介面來列舉符號存放區中的資料表。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 本範例將示範一般的函式，使用`getEnumTables`來取得特定的列舉值物件的方法。  如果找不到此列舉值，函數就會傳回指標，就可以轉換到所要的介面。 否則，函數會傳回`NULL`。  
  
```cpp#  
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)  
{  
    IUnknown *pUnknown = NULL;  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumTables> pEnumTables;  
        if (pSession->getEnumTables(&pEnumTables) == S_OK)  
        {  
             CComPtr<IDiaTable> pTable;  
             DWORD celt = 0;  
             while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&  
                   celt == 1)  
             {  
                  if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)  
                  {  
                       break;  
                  }  
                  pTable = NULL;  
             }  
        }  
    }  
    return(pUnknown);  
}  
```  
  
## 請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)